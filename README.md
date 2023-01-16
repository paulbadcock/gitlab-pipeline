# gitlab-pipeline
Custom pipelines for different solutions

# RedHat Advanced Cluster Security (ACS) Scanner

This scanner allows you to use [ACS](https://www.redhat.com/en/technologies/cloud-computing/openshift/advanced-cluster-security-kubernetes)/[StackRox](https://www.stackrox.io/) to drive auditing and compliance.

Note: allowing the build to fail should be allowed as ACS has the ability to flag a rule to break pipelines if detected.

Two CI/CD variables need to be defined

Variable| Example    | Description
--------|------------|-----------------
STACKROX_CENTRAL_HOST | central.my.tld | the address of the stackrox/acs server
ROX_API_TOKEN | A_SECRET | this API token with read/write to registry [per documentaton](https://docs.openshift.com/acs/3.73/integration/integrate-with-ci-systems.html#integrate-circle-ci_integrate-with-ci-systems)

To turn it on please place the following in your `.gitlab-ci.yml`

```yaml
  - project: 'https://github.com/paulbadcock/gitlab-pipeline.git'
    ref: main
    file: 'acs-scanner.yml' # RedHat Advanced Cluster Security compliance
```

