---
title: "Basic Wired Network Config Problem"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by erik.klingman on 2008-03-18
I am setting up a new server for a client on site, and just finished installing 7.10.  The problem is that I know the network settings are right, but I can't seem to do anything that requires network connectivity.  Here is my /etc/network/interfaces:


# The primary network interface
auto eth0
iface eth0 inet static
address 132.x.x.x
gateway 132.x.x.x
netmask 255.255.255.192


And here is my /etc/resolv.conf:

nameserver 132.x.x.x
nameserver 128.x.x.x


I restart the network with /etc/init.d/networking restart successfully, but whenever I try to ping, say, [www.google.com](www.google.com), it comes back with an unknown hostname error, and whenever I try to ping another server on the same network, it says the destination host is unreachable.

I know the cable and settings work; I'm using them right now on my MacBook Pro to post this thread.  I've gone all over the forums and the web, trying to figure out what else I need to change to get this to work.  No proxy settings that I know of, the settings are correct, service restarts successfully, etc.  I'm wondering if there is anything anybody knows about that I'm not checking, or if it's possibly a bug in 7.10?  

Thanks in advance for any help.

---

### Post by Eiríkr on 2008-03-18
Could you post what [font=courier]ifconfig[/font] shows on Ubuntu?  It should display the current state of your interfaces, which will (hopefully) provide a clue.  

Cheers,

Eiríkr

---

### Post by Iowan on 2008-03-19
> **erik.klingman said:**
> ... and whenever I try to ping another server on the same network, it says the destination host is unreachable.
Will it ping by address?

---

