---
title: "Ubuntu on VMWare Wrksation..Help to set up internet"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by vpp84 on 2007-10-09
hi,

am using ubuntu 7.04 and i've installed it on VM Ware workstation which is on XP Professional.

Now i want to know how do i start my net/internet on ubuntu?

On XP i connect via PPPOE connection.

I've set da VMNET tcp/ip to obtain automatically and i've also selected the VMWare bridge connections option under network properties of XP.

Kindly guide me starting the internet connection on ubuntu which is on vmwareworkstation..

P.S: Am new to using Ubuntu and thz da reason why i installed it 1st on VM Ware workstaion.

Thanks in advance..

Peace to all.

---

### Post by conjur3r on 2007-10-09
Set up the VM to have NAT networking.  Next time your Ubuntu box gets networking information, it should have all it needs to access the internet.  With this setup, the XP box appears as a "router" to the VM.

When you have your new networking settings, try a ping to both google.com and its ip address of 64.233.167.99.  If both work then rejoice!  If only the IP work then you have DNS issues.  If none work then :(

---

