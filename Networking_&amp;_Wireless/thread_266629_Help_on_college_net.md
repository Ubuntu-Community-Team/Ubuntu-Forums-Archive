---
title: "Help on college net"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by gironja on 2006-09-27
Hi!

I'm using right now my laptop's wireless to connect at college's network, but  it is not a stable connection since a few weeks, so sometimes I try to use the ethernet (cabled). At one lab I can do it, since it is DHCP, but at the rest, all PC's have static IP's. It has been possible to get connected only 2 or 3 times configuring eth0 with the PC's IP, NETMASK, and GATEWAY. But almost everytime (all but 2or3times), network manager applet, and the default network applet shows a connection, but there's no transfer. 

Is there a way to get rid of this, and make possible a connection through eth. cable? I think this is much to ask, but I'll do it anyways:) Is there a way to plug in the cable, and "scan" it to get the IP, Netmask, and gateway?


Thanks for all!!!



jna

---

### Post by kidders on 2006-09-27
Hi there,

Chances are that if certain parts of your college LAN don't provide a DHCP service, then you're not supposed to plug your PC in there! It is often possible to do so anyway, as long as you can find an unallocated IP to use. You would copy the other configuration details from another PC that is already connected.

---

### Post by gironja on 2006-09-28
You are right! Static = no DHCP... but what seems weird is that even copying the other computer's config (IP, Netmask, Gateway),and using it's cable (so the server "see" mine as if it is the original one), I could not have any connection... :( and that's what I'm looking for.. a way to have working that possibility... 

About the unallocated IP... I haven't thought of that! I'm gonna try that! Thanks! :D

---

### Post by kidders on 2006-09-28
Hi again,

If copying another PC's network settings and stealing its cable fails, chances are that you are being blocked on the basis of your MAC address. *Be aware that even attempting that will get you expelled from many colleges.* There are ways of further experimenting with gaining unauthorised access to a network, but it wouldn't really be appropriate to discuss them here.

---

### Post by gironja on 2006-09-28
LOL! yes... that may sound as law infringment. But as fas as I am concerned, some IT personnel do permit students to use cables, but taking precautions: put back the used cable, re-config the laptop for dhcp (so, if connecting to other's cable the IPs won't have any conflict), etc. But I know it is an issue of static IP'ing, since once in my home's net I used static, ad was not always an easy task to put another PC on a cable belonging to other PC...

---

