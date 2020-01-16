tripleo-container-image-delete
==============================

A role to perform the container image delete against a registry.

Requirements
------------

None.

Role Variables
--------------

* `tripleo_container_image_delete_become`: (Boolean) Run as root. This needs to be true if deleting from the local registry. Default: true
* `tripleo_container_image_delete_debug`: (Boolean) Flag to print out the delete command. Default: False
* `tripleo_container_image_delete_image`: (String) REQUIRED. Full URL of image to be deleted in the form <fqdn>:<port>/path/to/image.
* `tripleo_container_image_delete_password`: (String) Password for the registry
* `tripleo_container_image_delete_registry_url`: (String) Registry to run the delete against. Should be in the form <fqdn>:<port>.
* `tripleo_container_image_delete_username`: (String) Username for the registry
* `tripleo_container_image_delete_yes`: (Boolean) Do not prompt for configuration. Default: true

Output Variables
----------------

* `tripleo_container_image_delete_result`: Ansible execution results

Dependencies
------------

None.

Example Playbook
----------------

Example container delete execution playbook

    - hosts: undercloud
      gather_facts: true
      tasks:
        - name: Delete containers
          import_role:
            name: tripleo-container-image-delete
          var:
            tripleo_container_image_delete_image: undercloud.ctlplane.localdomain:8787/library/centos:7

License
-------

Apache-2.0