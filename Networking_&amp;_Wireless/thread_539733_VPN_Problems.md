---
title: "VPN Problems"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by eArquilla on 2007-08-31
I successfully installed vpcn
Clicked on Network Manager
Configure VPN

Add
Imprted my saved configuration
Ok

So i go to actually connect to the network, it asks for my password and group password, i click OK.... and then it crashes. By crashing I mean the icon disappears and I have to type NetworkManager in terminal to get back online.

I'm running Ubuntu Feisty 64 bit

I've been searching and found someone with my same problem but no solution was posted.

Help please!

---

### Post by kansei on 2007-09-18
There is a patch available that fixes this:

[https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/124238](https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/124238)

The bug is still present in the package, even in Gutsy!

make sure the package 'fakeroot' is installed before you go through the steps to patch it.

---

