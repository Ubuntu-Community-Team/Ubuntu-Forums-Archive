---
title: "Wireless problems on HP dv6000"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by guardianx3 on 2008-09-26
I have a HP dv6000 laptop.
I installed ubuntu and the wireless internet stopped working.
I tried looking for the problems online but failed.
Someone please help me :) Thank you
By the way, I'm a first time ubuntu noob.

---

### Post by jmbargar on 2008-09-26
It would be interesting that you could add some information about your wireless card (vendor and model) or the iwconfig and ifconfig output. Anyway, you can find a lot of links about the wireless configuration on Ubuntu systems (searching by Google) like this:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Good luck!

---

### Post by guardianx3 on 2008-10-18
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev02)

Subsystem: Hewlett-Packard Company Unknown device 1374
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at b6000000 (64bit, non-prefetchable) [size=16k]
Capabilities:<access denied>

Thats what I get if i type in " lspci -v | less "

Once again, I remember using wireless once before.. and then it just stopped working.

---

### Post by Ayuthia on 2008-10-18
Can you post your kernel version and lshw -C network information:
```
uname -a
lshw -C network
```
There have been some kernel updates that might provide another driver for you to use and possibly fix the b43 driver.

---

### Post by guardianx3 on 2008-10-18
When I type in uname -a... I get:
Linux chris-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

When I type in lshw -C network.. I get:
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:bc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Ayuthia on 2008-10-18
I think that the solution is in 2.6.24-21-generic.  If you have a wired connection, you can install the updates and your wireless might work.  If it does not, there is another driver there that will work.  You can find it in System->Administration->Hardware Drivers.  The new driver is the Broadcom STA.  

If you do not have a working wired connection, your next option would be to download the driver from :
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

You might need to have build-essential installed.  That is found on the install CD if you have it.  The instructions can be found in the Readme.txt at that website.

Hope that helps.  If you get stuck anywhere, just come back and we can see what can be done.

---

### Post by guardianx3 on 2008-10-18
> **Ayuthia said:**
> I think that the solution is in 2.6.24-21-generic.  If you have a wired connection, you can install the updates and your wireless might work.  If it does not, there is another driver there that will work.  You can find it in System->Administration->Hardware Drivers.  The new driver is the Broadcom STA.  
.

Yes, that did it for me. My wireless finally works again! Thank you very much~

---

