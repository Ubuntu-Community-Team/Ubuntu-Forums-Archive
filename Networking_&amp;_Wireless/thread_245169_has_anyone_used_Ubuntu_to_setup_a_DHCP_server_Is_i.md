---
title: "has anyone used Ubuntu to setup a DHCP server? Is it possible with Ubuntu?"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-08-27
First off, here's my ultimate aim
[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

So I want to use my Ubuntu box as a router, and since my eth0 is connected to my cable modem,I thought I would use eth1 as my private side LAN interface, and connect it to a switch. 

So I used apt-cache to search for some dhcp servers, and all of them appear to be buggy in that they assume both my eth0 and eth1 have to listen for DHCP broadcasts. 

How do I tell any DHCP server that my eth0 is actually a client and only eth1 needs to be a dhcp server?

---

### Post by f00buntu on 2006-08-27
Hi,

Install a dhcp server:

sudo apt-get install dhcp

then edit /etc/default/dhcp with your favorite editor:

gksudo gedit /etc/default/dhcp

there you can put the interface you want your dhcp server to listen on, for example:

INTERFACES="eth1"

Good luck with your router setup!

f00

---

