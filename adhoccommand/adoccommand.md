### adhoc commands
To put simply, Ansible ad hoc commands are one-liner Linux shell commands and playbooks are like a shell script, a collective of many commands with logic.
Ansible ad hoc commands come handy when you want to perform a quick task.

# in the  the webservers group inside the inventory
ansible -i inventory dbservers -a "ls"   
### check for the list of items and hidden files on the target machines
ansible -i inventory all -a "ls -lart"
# Get ping all serves
ansible -i inventory all -m ping
### now create directory templates on all machines
ansible -i inventory all -a "mkdir templates"
### to create a file text.txt on all machines
ansible -i inventory all -a "touch templates/text.txt"
### To remove cloud folder
ansible -i inventory all -a "rm -r -f secret"
### ### To check the disk/memory space on all hosts in an inventory file
ansible -i inventory all -m shell -a 'df -h'
### ansible ad hoc command to check the free memory or memory usage of hosts
ansible -i inventory all -a "free -m"

### To find ids on host machines
ansible -i inventory webservers -m shell -a 'id'

### first create a file touch /tmp/my-file.txt on the control server and push it to all #machines
touch /tmp/my-file.txt
###  to install apache on all machines
ansible -i inventory webservers -m apt -a 'name=apache2 state=latest'

### You can check the status of a specific service on single hosts or server1
ansible -i inventory webservers -m service -a 'name=apache2 state=started'