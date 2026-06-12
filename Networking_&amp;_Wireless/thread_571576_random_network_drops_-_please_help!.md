---
title: "random network drops - please help!"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by benma on 2007-10-09
my hardware is: 
2 PCs. One of them has WinXP, the other has WinXP and Xubuntu in dualboot.
EDIMAX ES3108P switch.  aztech 600e DSL modem/router - configured as router.
The xubuntu PC has a built in network card: Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC

The problem:
The problem doesn't exist when i dualboot to WinXP. I experience random network drops on xubuntu.
reseting the network with the next command shows no network available:
sudo /etc/init.d/networking restart
rebooting the PC solves the problen till the next random network drop.
In the same time when i experience the network drop, the network works fine on the another (winxp) PC.

Please help!!!

BTW, the xubuntu version is "feisty".

---

### Post by jonobr on 2007-10-09
If its a dual boot and the XP side is working fine, all things being equal its not a network problem,
and assume its a driver issue?

To be sure, (If this is happening often), you could initiate 3 simultaneous continous pings from terminal window,

One from the xubuntu to the other PC, one to the DSL router, the last to an external site that responds to ping.

When it happens again Im guessing all 3 connections will drop, pointing to something on the linux side, however, no harm to test this

---

### Post by raymcgill on 2008-07-10
I too have this issue. One large download and Boom. No connectivity.

---

