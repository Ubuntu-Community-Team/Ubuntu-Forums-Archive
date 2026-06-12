---
title: "Network/Ethernet NIC card"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by djdnc on 2007-12-14
I have a internal PCI type 10/100 ethernet/nic card that Ubuntu is not seeing. This is a regular wired type (RJ45/Cat5) type connection (not wireless). I think its the only thing that Ubuntu did not automatically recognize and configure on install. 
I am a newbie so please explain to me in simple (if possible) steps for how to get it to recognize the card.

---

### Post by ajgreeny on 2007-12-14
In a terminal type ```
lspci
``` to see what network card you have.  Was it online when you installed?  If not you may need to run ```
ifconfig up
``` as well.  Let us know if this is no help.

---

