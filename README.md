# apache-operator - ansible based

this operator can listen events and trigger the plabook. you can write your own login inside the playbook

documentation is here https://github.com/operator-framework/operator-sdk/blob/master/doc/ansible/user-guide.md


to test locally

operator-sdk up local

watches.yaml file

```

cat watches.yaml
---
- version: v1alpha1
  group: apps.example.com
  kind: Apache
  #role: /opt/ansible/roles/apache
  role: /products/operator/apache-operator/roles/apache

```

one of the BuildCinfig

``` 
kind: BuildConfig
apiVersion: build.openshift.io/v1
metadata:
  name: httpd-ex
  namespace: infra-test
  selfLink: /apis/build.openshift.io/v1/namespaces/infra-test/buildconfigs/httpd-ex
  uid: 04e33684-dbf7-11e9-b403-0a580a810020
  resourceVersion: '3618119'
  creationTimestamp: '2019-09-20T22:35:59Z'
  labels:
    app: httpd-ex
  ownerReferences:
    - apiVersion: apps.example.com/v1alpha1
      kind: Apache
      name: example-apache
      uid: f7e59560-dbf5-11e9-ad9d-0050569b4011
spec:
```

so the CRD is associated  with the config files you created automatially.



