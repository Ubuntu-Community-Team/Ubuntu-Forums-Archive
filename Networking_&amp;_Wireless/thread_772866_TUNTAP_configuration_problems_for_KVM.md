---
title: "TUN/TAP configuration problems for KVM"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by dehuszar on 2008-04-28
I'm having a hell of a time getting a machine to bridge properly so that my KVM/QEMU virtual image is part of the local network.  I've done this successfully on two Hardy desktops, but I can't get it to work on my new Hardy server (using the server install with a bare-bones gnome/GDM/XORG install).

Here are my config files: (the file names with dashes above and below are not in the files themselves.  Just trying to be as clear as possible.

taking a page from VirtualBox setups, I created a boot time TUN control script:

---------------
autotunctl.sh
---------------
#!/bin/bash

sudo tunctl -t tap0 -u $USER
sudo chmod 0666 /dev/net/tun
sudo brctl addif br0 tap0

IFNAME=tap0
sudo ifconfig $IFNAME 192.168.1.11 netmask 255.255.255.0 up

#load kvm modules
sudo modprobe kvm-amd
sudo modprobe tun

---

my KVM IFUP script file
------------------
/etc/kvm/kvm-ifup
------------------
#!/bin/bash

sudo /sbin/ifconfig tap0 0.0.0.0 promisc up
sudo /usr/sbin/brctl addif br0 tap0
sleep 2

---

my interfaces file
------------------------
/etc/network/interfaces
------------------------
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
address 192.168.1.10
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
bridge_ports eth0 
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
bridge_maxwait 2

auto eth0
iface eth0 inet manual

---

and finally, my virtual image launcher
-----------------------
~/.scripts/bbsrvrStart
-----------------------
# start kvm
IFNAME=tap0
kvm -hda /home/notes/images/BlackBerrySRVR.img -boot c -m 1024 -net nic,ifname=$IFNAME -net tap,ifname=$IFNAME,script=/etc/kvm/kvm-ifup

---

Hopefully, I'm just making a stupid mistake somewhere, but I can't get the guest OS to see the network AT ALL!!  :(  When it was set up as a NAT config, it worked- ...but that doesn't help me for my purposes.

Any help would be appreciated.  Thanks in advance.

--Sam

---

