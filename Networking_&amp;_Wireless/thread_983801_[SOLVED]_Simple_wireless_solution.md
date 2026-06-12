---
title: "[SOLVED] Simple wireless solution?"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by xadder on 2008-11-16
I found a simple solution to my wireless problems yesterday, which I just described in 

[http://ubuntuforums.org/showthread.php?t=981247]("http://ubuntuforums.org/showthread.php?t=981247")

(No driver installation required)
As there are so many people who seem to have lost wireless after an upgrade to Intrepid, I start a new thread here with the word "solution" in it in case it helps others. My machine was a Thinkpad T32, with lshw -C network giving:


description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:e0:ec:d7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

---

### Post by xadder on 2008-11-16
Just flagging as solved -- this solution may help others.

---

