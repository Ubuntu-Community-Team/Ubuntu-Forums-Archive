---
title: "Networking in Ubuntu Vagrant box"
date: 2015-06-16
forum: Networking &amp; Wireless
---

### Post by Maximilian_Brehm on 2015-06-16
Hey there, 


I am currently trying to set up an Ubuntu 14.04 Vagrant box using Virtual Box 4.3.28 that receives VRPN coordinates[1] from an outside server running Windows 7. The box's network is bridged to the host's network card that has both the host and the external server. The box can be ping the server, but the server can not ping the box. The box does not receive any data via VRPN. The host system can ping the guest and guest can ping the host. The box receives data via VRPN from a sample VRPN server on the host. I was able to ping the host and a Windows 8 guest VM from the external server.


The Vagrant file looks like this:


```
# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure(2) do |config|


        # To avoid an error, we add an hostname
        # Get more info here: http://blog.doismellburning.co.uk/2013/01/19/upgrading-puppet-in-vagrant-boxes/
        config.vm.hostname = "3d-sketch.hpi.de"


        # Enable port forwarding (this does not work since the server is not run locally
        # RepetierServer
        # config.vm.network "forwarded_port", host: 3344, guest: 3344
        # vrpn
        # config.vm.network "forwarded_port", host: 3883, guest: 3883


        # box's crossbar server
        config.vm.network "forwarded_port", host: 8080, guest: 8080


        # bridge for the magic...
        config.vm.network "public_network", bridge: "wlan0"


        config.vm.synced_folder ".", "/vagrant", disabled: true
        config.vm.synced_folder "../3d_sketch", "/vagrant/3d_sketch", create: true


        # for defining a name
        config.vm.define "3d_sketch_server" do |s|
        end


        config.vm.provider "virtualbox" do |vb|
                # https://serverfault.com/questions/453185/vagrant-virtualbox-dns-10-0-2-3-not-working?rq=1
                # https://serverfault.com/questions/495914/vagrant-slow-internet-connection-in-guest
                
                # vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
                # comment the following line if there are too many DNS lookups
                # vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
                
                # overkill to get all network devices into Promiscuous Mode
                vb.customize ["modifyvm", :id, "--nicpromisc0", "allow-all"]
                vb.customize ["modifyvm", :id, "--nicpromisc1", "allow-all"]
                vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
                vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
  end


end

```

Any ideas? Please find my network info file attached (generated with wireless-info).


Regards 
Max

[1] VRPN is a protocol for transmitting information of physical devices (position, orientation, etc.) via the network. This section may be interesting: [https://github.com/vrpn/vrpn/wiki/Troubleshooting-VRPN#no-unreliable-messages-seem-to-get-through-cant-send-udp](https://github.com/vrpn/vrpn/wiki/Troubleshooting-VRPN#no-unreliable-messages-seem-to-get-through-cant-send-udp)

---

### Post by Maximilian_Brehm on 2015-06-16
The firewall also doesn't seem to be the problem:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

