# reference-spring-boot-mvn-jkube-cloud-resources (Jenkins) (Workflow: Typical)
The cloud resources for the [reference-spring-boot-mvn-jkube](https://github.com/ploigos-reference-apps/reference-spring-boot-mvn-jkube)
application when using Jenkins and the Typical workflow.

## Install

### 0. Prerequisite

* TODO

### 1. Deploy Ploigos Kubernetes Resources

```bash
# this should be the namespace that Jenkins is running in
WORKFLOW_NAMESPACE=
helm dependency update charts/reference-spring-boot-mvn-jkube-workflow

helm secrets upgrade --install \
    reference-spring-boot-mvn-jkube-workflow-typ ./charts/reference-spring-boot-mvn-jkube-workflow \
    -f charts/reference-spring-boot-mvn-jkube-workflow/values.yaml \
    -f charts/reference-spring-boot-mvn-jkube-workflow/secrets.yaml \
    --namespace ${WORKFLOW_NAMESPACE} \
    --render-subchart-notes
```

### 2. Update Jenkinsfile

1. The helm chart run will have output `PGP Keys Secret: ${PGP_KEYS_SECRET}`, you need to update
the `pgpKeysSecretName` parameter in the Jenkinsfile in the associated project to this one
with that value.
2. TODO

### 2. Configure Jenkins

1. TODO
