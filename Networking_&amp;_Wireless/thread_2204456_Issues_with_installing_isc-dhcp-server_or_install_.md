---
title: "Issues with installing isc-dhcp-server or install update"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by wojciech2 on 2014-02-08
This is my last resort to get help. I have been at this for a week myself, read the net forums and still can't figure it out. It just doesn't want to work, I am extremely frustrated and hope someone can help.

When I run with or without sudo for @root;

apt-get isc-dhcp-server it returns;

apt-get install isc-dhcp-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package isc-dhcp-server

And

sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update

Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux
Version 2.30.2
Ubuntu
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"



Where do I start? I would really appreciate some help on this folks
Thank-you so much.

Already ran update and upgrade.

---

### Post by steeldriver on 2014-02-08
I don't think isc-dhcp-server was introduced into Ubuntu until after 10.04 - the DHCP server package in Lucid was dhcp3-server

---

