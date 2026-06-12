---
title: "Inconsistent Networking with Intel PRO/Wireless 2915ABG and Realteck RTL8196/8110"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by syhu on 2005-10-23
Hello,

I've been considering a switch from XP to Linux for a while and had found Ubuntu recently. The Ubuntu Philosophy clicks with my idea of what software should be..  so I felt compelled to give it a try.

I'm using a BenQ Joybook S72 (a laptop) with one wired and one wireless network card. The cards are:

Intel(R) PRO/Wireless 2915ABG 
Realteck RTL8196/8110 Family Gigabit Ethernet NIC

However, DHCP didn't work during installation, but after boot up they were visible from network-admin, so I manually configure both cards for DHCP and both worked for a while. 

But, after another boot-up both network cards stopped working. I tried rebooting, deactivate/reactive the cards, testing one at a time (disabling the other), even specified forced IP (as opposed to DHCP assignment), but none of the network cards was able to work again.

Both work okay without problem in XP, so I suppose it's not a router problem.

typing 'dmesg' shows that somehow the system is looking for a IPv6-capable router but cannot find one. But i cannot find where to configure the card to be IPv4 only.

Any help/suggestion is appreciated. Thanks!

---

### Post by iinstalledubuntunaked on 2006-03-01
hi there,

i am the proud owner of an s72 too. i stumbled across this thread vir google because i had the same problem.

the s72 has some irq problems. i found these sites about the s72 and problems with linux installation:

[http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html](http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html)
[http://www.schwerdaeus.de/jbs72/](http://www.schwerdaeus.de/jbs72/)

this is what i did:
-installed ubuntu
-got into to the root konsole with "sudo so"
-edited the /boot/grub/menu.list: you have to add irqpoll to every line beginning with kernel

---

