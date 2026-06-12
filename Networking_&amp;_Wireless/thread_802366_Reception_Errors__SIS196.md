---
title: "Reception Errors / SIS196"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by olbion on 2008-05-21
Hi all,

I have a Fujitsu V5535 laptop on to which I have installed Ubuntu 8.04. After some fixing, most of it is working fine, however I'm having troubles with the wired network interface, namely this:

I can use the network to access the internet. However, if I try to access another Ubuntu machine in my local network I get a timeout error. Likewise, if another Ubuntu machine is trying to access me, the same error occurs.

Using System > Administration > Network Tools I have noticed something that may be of interest. First I select eth0 as Network device. When another machine is trying to connect to mine, the number next to the text Reception Errors increases. It seems that the other machine is trying to connect, and that each time a reception error is reported.

This affects for example Samba as well as XDMCP remote login.

I have tried using a different router, and it makes no difference. If I use the wireless connection on the laptop, it works fine. I have also booted with Vista to make sure that the network interface isn't physically damaged, and there it runs fine. So it seems to be a driver issue.

dmesg reports that "sis190 Gigabit Ethernet driver 1.2 loaded". According to my laptop specification, my network interface is sis196. Could this difference be the source of the problem?

Or is there anything else I can try?

Thank you very much in advance.

---

