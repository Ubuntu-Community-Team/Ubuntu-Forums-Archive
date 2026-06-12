---
title: "Cannot get Wifi Working"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by noobwifi on 2008-07-06
I have a Sony Vaio VGN-NR310E notebook computer with built-in Wifi... works fine under Vista.  The wireless is a Marvell built in card with Atheros chips.  Want to switch to Ubuntu/Linux.  I have tried just about everything to get Wifi working under Ubuntu... madwifi.. NDISwrapper... etc.  According to Ubuntu the drivers (HAL) are installed.  Nonetheless, I cannot browse local networks.  Help (please)!!!

---

### Post by noobwifi on 2008-07-06
This might help -- 

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by Midwest-Linux on 2008-07-06
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

It seems that the AR242X works with the same commands as the 5007 according to the above thread further down the page. If not, I'll try to find another link for you.

---

### Post by noobwifi on 2008-07-06
Didn't work. :(

---

### Post by noobwifi on 2008-07-06
Also, my laptop has a toggle switch for wireless on/off.  In Vista, when the toggle is on, there is a light indicator on the laptop.  In Ubuntu, the light does not work.  Hmph.

---

### Post by noobwifi on 2008-07-06
laptop:~$ sudo lshw -C network
[sudo] password for mallinj: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:b8:da:96
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=24.169.230.76 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
laptop:~$

---

### Post by Mindcrime13 on 2008-07-22
same issue here, do you got any updates?

---

