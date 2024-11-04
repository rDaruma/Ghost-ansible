# Ghost Ansible
A quick ansible script for setting up a Ghost blog, mainly suited for use on DigitalOcean droplets.

## Setup
Modify ```YOUR_SSH_USER``` in group_vars/web.yml

In templates/nginx.conf.j2, modify the following values:

* [YOUR_WWW_DOMAIN_NAME]
* [YOUR_DOMAIN_NAME]

Modify ```YOUR_SERVER_IP``` in hosts

Put your SSL cert and key to files folder as server.crt and server.key

Run the setup script with ```ansible-playbook ghost.yml```

SSH into your droplet, run mysql setup ```sudo apt-get install mysql-server```

CD to your ghost directory and setup ghost ```ghost install```

During the ghost install script, when prompted whether you want to set up Nginx and SSL, answer 'N'.

## What This Does

* Sets server timezone
* Sets up a 1gb swap (disable import swap task in ghost.yml if you don't want swap)
* Installs and sets up Nginx and config file
* Uploads SSL cert and key
* Installs MySQL, NodeJS and Ghost.

## See Also
I first wrote about this in my blog post here:
[https://cerealaftermilk.com/automate-ghost-install-with-ansible/](https://cerealaftermilk.com/automate-ghost-install-with-ansible/)