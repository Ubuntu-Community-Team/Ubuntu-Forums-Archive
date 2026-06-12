---
title: "IBURST PCMCIA and 7.10"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by r0bertf on 2008-01-16
Hi all,
I've been searching for a solution to install the IBURST PCMCIA Card and get it working on Ubuntu 7.10  All the other docs seem to point to earliver versions / kernels.

is there anyone out there that's got the card working in 7.10?

please help!!!

Thanks in advance

---

### Post by nic2 on 2008-03-08
I managed to get my newly acquired iBurst PCMCIA card working by following steps 1 to 7 on the howto by Skrewdriver - follow link below for details

[http://ubuntuforums.org/showthread.php?t=305020&highlight=iburst]("http://ubuntuforums.org/showthread.php?t=305020&highlight=iburst")

Step 8 of Skrewdriver's Howto unfortunately did not work for me and I downloaded the Roaring Penguin PPPOE dialer at [http://www.roaringpenguin.com/products/pppoe]("http://www.roaringpenguin.com/products/pppoe") (as recommended in the MobileWirelessBroadband page in the Ubuntu User Documentation located at [https://help.ubuntu.com/community/MobileWirelessBroadband?highlight=%28iburst%29]("https://help.ubuntu.com/community/MobileWirelessBroadband?highlight=%28iburst%29")).

I then followed the Dialer configuration as per the MobileWirelessBroadband page but it also did not work - after following the instructions in the Readme and doc/How-To-Connect pages contained in the rp-pppoe-3.8 folder the PPPoE connection worked fine (deleting the 'auto ib0' line in /etc/network/interfaces config file was the crucial step to get the connection going).

Good luck with this - hope you are connected to the iBurst network soon :)

---

