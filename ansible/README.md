To deploy infrastructure first you have to configure an environment. 

	You have to update file ./inventories/dev/hosts

After finishing creating hosts file you can start configuration of environment.

	ansible-playbook -i ./inventories/dev/hosts ./envconfig.yml

To install DB and Docker registry please use next command:

	ansible-playbook -i ./inventories/dev/hosts postgres.yml registry.yml

To install Jenkins you should first build docker image and after that you can run next command:

	ansible-playbook -i ./inventories/dev/hosts jenkins.yml

To install Docker images of project you should run command below:

	ansible-playbook -i ./inventories/dev/hosts awd.yml

Ansible Directory Layout

        .
        ├── README.md
        ├── awd.yml
        ├── envconfig.yml
        ├── inventories
        │   └── dev
        │       ├── group_vars
        │       │   └── all.yml
        │       └── hosts
        ├── jenkins.yml
        ├── postgres.yml
        ├── registry.yml
        └── roles
            ├── awd
            │   ├── backend
            │   │   ├── defaults
            │   │   │   └── main.yml
            │   │   ├── tasks
            │   │   │   └── main.yml
            │   │   └── vars
            │   │       └── main.yml
            │   └── frontend
            │       ├── defaults
            │       │   └── main.yml
            │       ├── tasks
            │       │   └── main.yml
            │       └── vars
            │           └── main.yml
            ├── common
            │   ├── handlers
            │   │   └── main.yml
            │   └── tasks
            │       ├── main.yml
            │       ├── ntp.yml
            │       └── pkg.yml
            ├── docker
            │   ├── handlers
            │   │   └── main.yml
            │   ├── tasks
            │   │   ├── main.yml
            │   │   └── pkg.yml
            │   ├── templates
            │   │   ├── daemon.json.j2
            │   │   └── docker.j2
            │   └── vars
            │       └── main.yml
            ├── jenkins
            │   ├── handlers
            │   │   └── main.yml
            │   ├── tasks
            │   │   └── main.yml
            │   └── vars
            │       └── main.yml
            ├── postgres
            │   ├── handlers
            │   │   └── main.yml
            │   ├── tasks
            │   │   └── main.yml
            │   └── vars
            │       └── main.yml
            ├── registry
            │   ├── handlers
            │   │   └── main.yml
            │   ├── tasks
            │   │   └── main.yml
            │   └── vars
            │       └── main.yml
            └── registry-ui
                ├── handlers
                │   └── main.yml
                ├── tasks
                │   └── main.yml
                └── vars
                    └── main.yml  
