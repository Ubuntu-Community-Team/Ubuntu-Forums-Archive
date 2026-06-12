---
title: "Wireless Connection Problem (Ubuntu 9.10 on Dell Latitute D450)"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by rn_huang on 2009-11-27
Hi, everyone.

I am new to Ubuntu. My laptop is Dell Latitude D450 and I was using Window XP. I just installed Ubuntu 9.10. Everything works perfectly except the wireless connection. (I can use the wired/wireless in window Xp and use the wired connection in Ubuntu.)

1) It seems that I "can" connect to the internet. I mean, I found the wireless network listed in the "Network manager". And I can click it to get me laptop connected. It seems working and the icon even shows the strength of the signal.

2) I can neither open any webpages nor update/install any programs from synaptic. 

3) I checked "System -> Administrator -> Hardware Drivers" but there's nothing listed.



Can any one help out? Thanks a lot!


Huang






P.S.:  Listed below is the result when I run "sudo lshw -C network". 


*******************************************************************************************

huang@ubuntu:~$
  **network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:fc:29:e1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt*fd 100bt 
100bt*fd
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5751*
v3.29a
       resources: irq:16 memory:dfdf0000*dfdfffff
  **network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:46:54:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 
(Dec
wireless=IEEE 802.11g
       resources: irq:17 memory:dfcff000*dfcfffff
huang@ubuntu:~$

*******************************************************************************************

---

### Post by cariboo on 2009-11-28
Open a terminal and type:

```
ping www.google.com
```

If the above command doesn't work, try:

```
ping 74.125.53.138
```

If the above command works, it means you have a dns problem.

---

### Post by woodnymph on 2009-11-28
i had trouble with a broadcom chip as well.  since you seem to have a wired connection, use it to run the update manager.  see how your wireless goes from there .. it worked for me.

---

