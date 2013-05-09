.. contents :: :local:


Introduction
------------

This is a Proof of concept for deploying Plone [http://www/plone.org] with Juju [https://juju.ubuntu.com]
as a local setup with lxc container.

Tested on Ubuntu 13.04 with 12.04 lxc container.

Requirements
------------

Follow this tutorial to getting started, configuring a local environment:

https://juju.ubuntu.com/docs/getting-started.html

Getting the Charm
-----------------

Creating a local directory for your charms, for example a directory with the name charms::

        mkdir ~/charms

Since this charm is for Ubuntu Precise we now create in our directory charms a second directory with the name precise::

        mkdir -p ~/charms/precise

Now clone the plone-charm into this directory::

        cd ~/charms/precise
        git clone https://github.com/svx/plone-charm plone

After this we are almost good to go ....

Changing the config
--------------------

As you can see we have a file called config.yaml in our fresh cloned plone directory,here you can change the password and the kind of setup [standalone vs zeo] as default the installation will use::

        password: admin
        plonemode: standalone <- change this to zeo if you want to use zeo

Deploying
---------

If you haven't already done, it' now time to bootstrap juju, if you did that already skip that::

        juju bootstrap

and now do the deploy::

        juju deploy --reository=~/charms local:plone

This will deploy Plone with all its dependencies on a fresh lxc container on your local machine,you can check the status with::

        juju status

This will take a couple of minutes, when its done you will see with 'juju status' something like::

        agent-state: started
        ...
        ...
        public-address: $IP

Now open a new browser and browse to $IP:8080 and have fun

**Please note:**

I only tested the $USER install of Plone, installing as root is not tested and I guess it will not work.

This is really just a 'quick and dirty' proof of concept for now, there is plenty of room for tweaking and making things nice, even this readme needs some improvements and formating :)



