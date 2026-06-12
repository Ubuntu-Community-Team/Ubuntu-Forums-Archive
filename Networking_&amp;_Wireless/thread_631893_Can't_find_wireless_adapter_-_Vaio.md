---
title: "Can't find wireless adapter - Vaio"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by kball on 2007-12-04
Hi all.  New to this forum and ubuntu, but not to Linux.  I've searched, used the HOWTO's and such and can't find the answer to my specific issue.

When I did the initial install of ubuntu on this Vaio PCG-K45 I swear the wifi nic was there.  I even successfully connected it to my router.  It's builtin to this model.  But after installation and restart, I can't find it in the NetworkManager.  Get the following from lshw.  I suspect it's finding it but doesn't know what to do with it.  I've found loads of info on how to configure it once the system has found it, but can't get past this issue.  Ubuntu 6.10.

  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:34000000-3400ffff

I'd truly appreciate any assistance.  I've heard good things about ubuntu, but if I can't get this wireless going it doesn't do me much good.

Thanks in advance
Ken

---

### Post by AngelAir on 2007-12-18
Hello,  I am also new here and also to Linux; but I was having a problem with my system not keeping the wlan card on after rebooting and found this HowTo:  [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)  Hope this can help you.  It sure helped me:)

---

