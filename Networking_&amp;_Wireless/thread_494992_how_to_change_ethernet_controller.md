---
title: "how to change ethernet controller?"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by ramsblues on 2007-07-07
Hi! 
         I am running a ubuntu 6.0.6 server on VMWare runing on a AMD machine. Today I copied the VM to run with a intel xeon server. Everything seems to be working fine except the network card. I got following error :

eth0: ERROR while getting interface flags : No such device.

The NIC card that I am trying to use is : Intel 1000 PRO. 

When I try to see what Ethernet Controller ubuntu OS is using with  lspci, I get:
Ethernet Controller: Advanced Micro Devices [AMD] 79c970 ( The NIC card that my previous machine - AMD computer uses).

How can I change the Ethernet controller to Intel 1000 PRO?

I tried modprobe e1000 command and putting e1000 in /etc/modules, its not working.

Appreciate any help,

---

### Post by ramsblues on 2007-07-07
FYI -
Resolved the issue. The problem was the wrong MAC address in etc/iftab. Changed the mac address to the new  NIC card and everything started working.

Thanks anyway.

---

