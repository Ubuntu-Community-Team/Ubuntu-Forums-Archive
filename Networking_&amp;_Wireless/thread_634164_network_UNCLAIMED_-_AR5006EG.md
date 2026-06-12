---
title: "network UNCLAIMED - AR5006EG"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2007-12-07
Hi

I'm working on installing Ubuntu 7.10 on my laptop Asus X51R and have done some checking what things are working with the ubuntu live cd. Problem is that the wireless network wont start, it don't even show up in network settings.

I tested the command lshw -C network and got the following

> 

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:08:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:7f:d4:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes



I'm using a ZyXEL p-320w.

How can i get the wireless network working?

---

### Post by overdrank on 2007-12-09
Hi and I have a similar wireless card in my laptop and vista says it is a 5007 and Ubuntu says it is a 5006. This link has helped some with the card in Gutsy and I hope it will provide some help
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by formol on 2007-12-11
hello,

i've the same problem.

i found a link to that [http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf) on the french version of ubuntu-forum. the guy seems and claim to have try many things but only ndiswrapper works. 

personnaly, it dont works now, but it's probably because i've to uninstall madwifi...

formol



(this post in french [http://forum.ubuntu-fr.org/viewtopic.php?id=170292](http://forum.ubuntu-fr.org/viewtopic.php?id=170292))

---

### Post by formol on 2007-12-11
here is what i have now, testing on the livecd

root@ubuntu:/etc/ndiswrapper# ndiswrapper -l
ar5211.sys : invalid driver!
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
net5211.inf : invalid driver!

i entered : ndiswrapper -i net5211.inf and the ar5211.sys was present on the folder.
i reed somewhere that a guy made it work with : ndiswrapper -i net5211 (without the .inf) and it work.  i tryed that too, but it didnt worked.  so, if any of you have any info about that, thx

---

