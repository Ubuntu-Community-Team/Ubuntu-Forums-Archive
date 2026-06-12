---
title: "Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) problem."
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Renato Souza on 2007-09-03
Hello

I have a HP pavillion dv2210us laptop which has a  Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01).

I managed to get it working with ndiswrapper, but after I used it once it disconfigured and the light on the device went yellow indicating that the hardware is turned off.

I reinstalled the driver but now when I go to System--> administration--> network 
The wifi doesnt appear there, so I cant configure IP or find any connections around.

Can someone please help me fix this issue?

Thank you.

---

### Post by Renato Souza on 2007-09-03
I seem to have fixed it with the help of a member from the brazillian ubuntu channel #ubuntu-br

First, he told me to 

lsmod |grep bcm 

then he said for me to 

lsmod |grep ndis

since none of them returned anything, he figured the modules for ndiswrapper werent loaded.

so I

sudo modprobe ndiswrapper

And that fixed it. 

Next he told me to add ndiswrapper to the bottom of /etc/modules so the modules would go up at boot.

Thanks for everyone that helped, and a special thanks to Cypherbios.

---

