=====
Usage
=====


To develop on towerlib:

.. code-block:: bash

    # The following commands require pipenv as a dependency

    # To lint the project
    _CI/scripts/lint

    # To execute the testing
    _CI/scripts/test

    # To create a graph of the package and dependency tree
    _CI/scripts/graph

    # To build a package of the project under the directory "dist/"
    _CI/scripts/build

    # To see the package version
    _CI/scipts/tag

    # To bump semantic versioning [major|minor|patch]
    _CI/scipts/tag major|minor|patch

    # To upload the project to a pypi repo if user and password is properly provided
    _CI/scripts/upload

    # To build the documentation of the project
    _CI/scripts/document



To use towerlib in a project:

.. code-block:: python

    from towerlib import Tower
    tower = Tower('hostname', 'username', 'password')

    # access hosts
    for host in tower.hosts:
        print(host.name)

    # access groups
    for group in tower.groups:
        print(group.name)

    # access inventories
    for inventory in tower.inventories:
        print(inventory.name)

    # access organizations
    for organization in tower.organizations:
        print(organization.name)

    # access users
    for user in tower.users:
        print(user.username)

    # access projects
    for project in tower.projects:
        print(project.name)

    # access teams
    for team in tower.teams:
        print(team.name)

    # all the above entities support creation and deletion either from the core tower object
    # or from their respective parent object.
    # eg: create a host
    tower.create_host_in_inventory('inventory_name','host_name', 'host description', 'variable_json')

    # or
    inventory = tower.get_inventory_by_name('inventory_name')
    inventory.create_host('host_name', 'host description', 'variable_json')
