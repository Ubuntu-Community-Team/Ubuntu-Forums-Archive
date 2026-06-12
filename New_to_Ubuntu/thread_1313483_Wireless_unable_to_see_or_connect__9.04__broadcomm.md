---
title: "Wireless unable to see or connect  9.04  broadcomm"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by jbonness on 2009-11-03
Can not see any  wireless networks, though can connect direct.  checked drivers, and backport download,  I am new at this, and using 9.04 on a dell.  Here is a screen shot.  Trying to connect to a ATT 2 Wire.  Thoughts
 *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:ce:57:ae:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0b:32:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.64 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:53:5c:3d:89:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by wrgb2 on 2009-11-03
You might try reinstalling the driver.  this has worked for me before.

---

### Post by LarsW_Tierp on 2009-11-03
Hi
Take a look at thread : [Wireless not working #2.]("http://ubuntuforums.org/showthread.php?t=1049761&highlight=broadcom")
It may help you.

---

### Post by anewguy on 2009-11-04
You say you checked the drivers - are you using the restricted driver from system/administration/hardware drivers?  If so, what exact driver does it say is enabled?  If not, what driver did you install and how (example, if you used ndiswrapper you have to blacklist several things to "disable" the built-in driver, etc.)?

Dave :)

---

