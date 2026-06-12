---
title: "Google opens, but nothing else"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by portujoel5 on 2007-05-12
I installed Ubuntu in a new HD, and I'm using the default setup. I seem to be connected to the web, but only google and some other pages open, but the search results from google won't open. In winXP I can open all, so It can't be my connection. 

I'm using AMD 64bits 3500+ and I connect to the web with the integrated card in my A33G motherboard. 

Help, please?

---

### Post by Vousmanos on 2007-05-13
I have the exact same problem... another computer on my wireless network works fine. The netwrok configuration is via dhcp and i have tried a different server with the same result. On pinging an unreachable host I get the response: "filtered".

---

### Post by portujoel5 on 2007-05-13
Well, I've tried some things around, and I did
```
sudo pppoeconfig
``` 

and the result of that "Wizard" sort of thing was that my device was unreacheable, or it didn't supported a PPPoE configuration or it was being used. Can't find a fix

---

### Post by portujoel5 on 2007-05-18
found a fix... but i need to type this eveytime I reboot

at terminal:

sudo su
sudo ifconfig eth0 mtu 1492
sudo ifconfig lo mtu 1492

this fixed my problem

---

### Post by heimo on 2007-05-18
> **portujoel5 said:**
> 
sudo su
sudo ifconfig eth0 mtu 1492
sudo ifconfig lo mtu 1492


You could probably put that stuff in /etc/network/interfaces. Syntax isn't one-to-one with command line - but it's easy (man interfaces). Something like this - and this is just an example, your lines will be different:
```
iface eth0 inet static
       address 192.168.1.3
       netmask 255.255.255.0
       mtu 1492

```
And same for lo.

---

### Post by fatfranko on 2007-06-26
my friend has the same motherboard with the same problem.
thanks heimo, that worked great.  fyi, i just needed to change eth0 and it worked fine.  i just left lo alone.

changed my friend's to look like this:

iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
mtu 1492

thanks again!

---

