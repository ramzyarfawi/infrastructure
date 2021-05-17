# infrastructure
infrastructure tutorial

1 - clone your IAC repo from github : https://github.com/ramzyarfawi/infrastructure.git

2 - install ansible on Ubuntu.
	- https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu
	$ sudo apt update
	$ sudo apt install software-properties-common
	$ sudo apt-add-repository --yes --update ppa:ansible/ansible
	$ sudo apt install ansible

3-  check ansible version and inventeory location:
	rarfaoui@rarfaoui-ubuntu:~$ ansible --version
	=> 
	ansible 2.9.6
	  config file = /etc/ansible/ansible.cfg
	  configured module search path = ['/home/rarfaoui/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
	  ansible python module location = /usr/lib/python3/dist-packages/ansible
	  executable location = /usr/bin/ansible
	  python version = 3.8.5 (default, Jan 27 2021, 15:41:15) [GCC 9.3.0]

4- Configure Ansible
	- go to /etc/ansible and change permissions to allow modify ansible.cfg:
	  $ sudo chmod -R o+rw ansible.cfg
	- open the file and add the inventory location, by default it is: 
	   [defaults]
	   #inventory= /etc/ansible/hosts
	   you can keep this conf or replace it by this one if you want to use a specific file location:
	   [rarfaoui]
	   inventory = ./inventory

5 - create the following dir:
	- /home/rarfaoui/IAC/ansible/

6 - copy your IAC project to this dir:
	- sudo rm -rf dirName : force remove directory
	- cd /home/rarfaoui/IAC/ansible/
	- sudo git clone https://github.com/ramzyarfawi/infrastructure.git
	- add permissions to ICA project 
	  cd /home/rarfaoui/IAC/ansible/ 
	  $ sudo chmod -R o+rw infrastructure

7 - change inventory file :
    - add  this lines to your inventory "/etc/ansible/hosts": 
    [ubuntu]
	microk8s-cluster ansible_host=192.168.1.48

8 - Verify the inventory
	$ ansible-inventory -y --list

9 - 
