# Ansible Playbook for installing cassandra cluster

## PLaybook requirements
- Java jre 8

## Additional Components 
- Creating Snapshots

#  Information
The Playbook will install cassandra on specified hosts from hsots.yml.
After the completing the installation it will add the configuration from j2 template.
Once all the configurations are completed it will restart the cassandra and cluster will be up and running.

#  Steps to run the playbook:

1. Add the ip in hosts.yml for the number of nodes on which to install cassandra
2. In roles/cassandra/vars/main.yml 
	Add the seeds ip, these seeds will be added in cassandra's installation file ie: /etc/cassandra/cassandra.yaml
* seeds_var : 172.31.22.239
* seeds_var2 : 127.0.0.1
	* **NOTE**: To add more seeds increase the variable on this path for eg. seeds_var seeds_var2 seeds_var3 ... seeds_varN and also add these variables in **roles/cassandra/templates/cassandra.yaml.j2** file at line No 424 **{{ seeds_var }},{{ seeds_var2 }},{{ seeds_var3 }},{{ seeds_varN }}**
3. At last simply run the play book on desired node.
