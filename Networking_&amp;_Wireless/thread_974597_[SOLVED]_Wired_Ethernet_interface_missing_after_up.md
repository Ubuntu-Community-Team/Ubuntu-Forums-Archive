---
title: "[SOLVED] Wired Ethernet interface missing after upgrade UNCLAIMED"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by gmstalk on 2008-11-07
I run ifconfig and I no longer have eth0. 
lspci:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64

There are many more errors like this in dmesg
[    5.346790]  sda:b44: disagrees about version of symbol ssb_device_is_enabled
[    5.347601] b44: Unknown symbol ssb_device_is_enabled
[    5.347696] b44: disagrees about version of symbol ssb_pcicore_dev_irqvecs_enable
[    5.347698] b44: Unknown symbol ssb_pcicore_dev_irqvecs_enable
....

I assume my problem is with ssb and b44. I cannot blacklist ssb. I tried and it runs anyway. I even put rmmod in rc.local to no avail. I used b44 with the previous kernel  2.6.24-19 and 2.6.24-21 (this one broke wireless). 

Can anyone help?

---

### Post by gmstalk on 2008-11-10
Has anyone gotten their wired network connection functioning? This is a real problem for me since WPA enterprise will not function for me at work (works great at home). I need to use wired at work. Otherwise I have to go back to windows. 

This was working before the upgrade to 8.10.

---

### Post by gmstalk on 2008-11-14
Anyone? Seriously. This is a big problem. I have no wired Ethernet. What do I do?

---

### Post by gmstalk on 2008-11-14
This is fixed in 2.6.27-8. I went to system> administration> software sources, on the updates tab, I chose pre-released updates (intrepid-proposed). Then I ran the update manager and let it rip.

Make sure b44 is not in the /etc/modprobe.d/blacklist. Dmesg will show that b44 loads fine now. 

So I now have wireless and wired working on 8.10. I feel much better. 

Now how do I mark this a resolved?

---

