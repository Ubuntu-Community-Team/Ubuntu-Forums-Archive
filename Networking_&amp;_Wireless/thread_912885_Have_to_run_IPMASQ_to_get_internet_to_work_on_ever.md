---
title: "Have to run IPMASQ to get internet to work on every boot"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by marcusjb on 2008-09-07
I know zero about ubuntu, but I'm trying to learn, and something changed on my system that when I boot to ubuntu, I have to run ipmasq in order to get online.

I'm running Ubuntu 8.04

I don't know what changed because it was over a month ago, I've just recently decided to deal with the frustration and come back to ubuntu.

---

### Post by tuga on 2008-11-12
Install firestarter and run the wizard: >firewall>run wizard.
I don't now why but this worked for me.

---

### Post by crashme on 2008-12-20
> **marcusjb said:**
> I know zero about ubuntu, but I'm trying to learn, and something changed on my system that when I boot to ubuntu, I have to run ipmasq in order to get online.

I'm running Ubuntu 8.04

I don't know what changed because it was over a month ago, I've just recently decided to deal with the frustration and come back to ubuntu.

I had this problem after a fresh install of Ubuntu 8.10. The problem is most likely that when ipmasq is run at boot, the network hasn't been configured yet. This could happen if you tried to use the network-manager GUI to set up the network.

I solved it by uninstalling network-manager and network-manager-gnome and configuring my network "manually" in /etc/network/interfaces.

It looks like this:

auto lo eth0 eth2
iface lo inet loopback

iface eth2 inet static
address 10.10.1.2
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255
gateway 10.10.1.1

iface eth0 inet static
address 10.10.10.10
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255

The startup is done by scripts that should already be present:

/etc/rcS.d/S40networking
/etc/rcS.d/S41ipmasq

I think something has changed in the network manager. I didn't have to do this in 8.04.

---

### Post by crashme on 2008-12-20
ipmasq isn't present in the default installation, by the way. It's only a problem for me because I do want to share an Internet connection through my computer, so I've installed it:

apt-get install ipmasq

---

