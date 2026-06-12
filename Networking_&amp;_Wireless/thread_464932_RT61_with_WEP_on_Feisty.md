---
title: "RT61 with WEP on Feisty"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2007-06-05
Hi!!

      I am unable to get my wireless card wwith the RT61 chipset working on Feisty. My office has a WEP network and I am unable to connect to it. The network does show up in network-manager, but the signal strength is show as zero and I am unable to connect. Can someone please help me with this???

---

### Post by MeeMaw on 2007-06-05
OK, the first thing I would check is to make sure the ESSID and WEP key are correct in your configuration file. 

This post says you have to edit your /etc/network/interfaces file with the correct information-
[http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)

but for WEP you should only have to put

iface ra0 inet dhcp
wireless-essid <my ESSID>
wireless-key <My WEP key>

I have an rt61 with WEP and it worked fine after I got it configured correctly.    ;)  

**Someone correct me if I'm wrong.** I'm typing from memory!!!! 
(I can't use Linux at work!!! I know I should be working, but everyone's entitled to a break!)

---

