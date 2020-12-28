# OpenShift Pipelines Operator
## 1. Code Repositories
https://github.com/openshift/tektoncd-pipeline-operator
## 2. Prerequisites

You must install these tools:

* go <br>
  https://golang.org/doc/install
* git
* oc <br>
  https://github.com/openshift/okd/releases/
* operator-sdk
  ```
  wget https://github.com/operator-framework/operator-sdk/releases/download/v0.17.2/operator-sdk-v0.17.2-x86_64-linux-gnu
  sudo chmod +x operator-sdk-v0.17.2-x86_64-linux-gnu
  sudo mv operator-sdk-v0.17.2-x86_64-linux-gnu /usr/bin/operator-sdk
  ```
* opm
  ```
  wget https://github.com/operator-framework/operator-registry/releases/download/v1.13.7/linux-amd64-opm
  sudo chmod +x linux-amd64-opm
  sudo mv linux-amd64-opm /usr/bin/opm
  ```
* yamllint
  ```
  sudo apt-get install yamllint
  ```
* dep
  ```
  sudo apt-get install go-dep
  ```

## 3. Build instructions

* Check out latest stable branch:

  ```
  git checkout v1.2.x
  ```

* The build is pretty straight forward. Just follow the instructions here:

  https://github.com/openshift/tektoncd-pipeline-operator/blob/master/docs/development.md

  Be sure that you are logged in to the destination image registry because the catalog image will be pushed there automatically.

## 4. Add operator to OKD's integrated OperatorHub

Apply the manifest from 

https://github.com/openshift/tektoncd-pipeline-operator/blob/master/samples/catalog-source.yaml

in your OKD cluster. Don't forget to adjust the location of the catalog image in the yaml file before! 

After a few seconds the operator will be available in the OperatorHub and you can install it.

## To Dos

* Do we have to rename the "OpenShift Pipeline Operator" (because it is a product from Red Hat) ?
* A clue should be added in the description of the operator that it can also be used for OKD.
* The image registry location should be replaceable from quay.io/USER to something more generic by using variable substitution in the build scripts, the CSV manifest and in the CatalogSource yaml in the examples directory.
* Create a Tekton Pipeline for this operator: "Eat your own dog food."
