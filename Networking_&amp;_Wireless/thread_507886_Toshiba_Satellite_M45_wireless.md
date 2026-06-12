---
title: "Toshiba Satellite M45 wireless"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by hbherman on 2007-07-23
I have not been able to connect wirelessly form my laptop using Ubuntu (Feisty). The internal wireless device can see the neighborhood routers and mine. However, I can't seem to connect to mine using the ssid and wep shared key that works in Windows XP. I was told the following output might help diagnose the problem:

harvey@ubuntu:~$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@05:04.0
       logical name: eth0
       version: 05
       serial: 00:12:f0:02:5a:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:b800b000-b800bfff irq:11

I was able to get a desktop to work with Ubuntu and an internal wireless card using ndiswrapper. I tried using the wireless device in the laptop both with and without diswrapper. No luck.

Any suggestions?

Harvey

---

### Post by hbherman on 2007-07-24
It's working now!
As suggested on this forum: take out everything on /etc/network/interfaces, except for lo.
Reboot and use network manager roaming to connect to the router.
Harvey

---

### Post by x34460 on 2008-01-09
i am having the same problem with the same model computer.
i did what was suggested here but with no success. problem still exists.
if anybody has discovered a solution, please post it here. 

thanks!

---

