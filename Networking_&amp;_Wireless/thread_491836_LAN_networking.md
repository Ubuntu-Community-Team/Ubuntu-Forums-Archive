---
title: "LAN networking"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Anant Khaitan on 2007-07-04
I have two system one loaded with Fedora Core 6 and other with Ubuntu 7.04, So I wanna setup a LAN connection between the two PCs for easy file sharing, internet sharing and others if any.. So if anyone can guide me through the steps/equipments required. Presently I just have a RJ45 Ethernet wire, I don't want to go to hardware shop for Router or Hub or whateva. Heard of Samba and NFS but I am a complete noob in the field of networking/LAN, so detailed instruction will be appreciated.

---

### Post by shuaibe on 2007-07-04
Hi,

There are many ways to do what you want to do, here is what I have in mind.

Get a switch from the shop and connect both your machines to it using straight ethernet cables.
Assign IP addresses to the network interface cards on both the machines such that they belong to same network. For example:
machine 1 : 192.168.10.1 Netmask 255.255.255.0
machine 2: 192.168.10.2 Netmask 255.255.255.0

Try to ping from both the machines to the other machine, if it works, then they are able to communicate.

For file sharing, best thing is to use ssh, you can easily find many details on how to install and use ssh on different How-Tos available on Ubuntu Wiki.

Hope it was helpful, good luck!

---

### Post by scxtt on 2007-07-04
you need a router to assign IPs, i don't think a switch can do that ... and he said he DOESN'T want a router ... he may be SOL aside from a crossover cable, but i don't have any experience w/ that ... in the long run a router is a MUCH better investment, esp. if your network expands ...

---

