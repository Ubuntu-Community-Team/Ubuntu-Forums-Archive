---
title: "Enable Wireless greyed out"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by djmac on 2009-07-27
I was using a wireless network and all of a sudden it dropped out and disappeared. When I go to look at the network manager, the 'Enable Wireless' was off and greyed out. I can't figure out how to enable wireless again.

 If it is any use, the output of lshw -C network was:

>  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:1b:fe:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:ce:fe:c3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:9d:27:2f:ef:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



Thanks

---

### Post by LookTJ on 2009-07-27
did you disable it by accident? do you have a switch or function key to enable the radio?

try ```
sudo iwlist wmaster0 scan
```

:)

---

### Post by djmac on 2009-07-28
I don't believe I disabled it by accident. 


Output of sudo iwlist wmaster0 scan:

> wmaster0  Interface doesn't support scanning.


Output of sudo iwlist wlan0 scan:

> wlan0     Interface doesn't support scanning : Network is down 

 For the record, the network is certainly not donwn!

Thanks

---

### Post by mapes12 on 2009-07-28
I'm guessing that your wifi card worked OK when Ubu was first installed and you did not have to mess around configuring ndiswrapper? Here are a range of support posts about your adapter:

[http://www.google.co.uk/search?hl=en&q=3945ABG+ubuntu&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=3945ABG+ubuntu&btnG=Search&meta=)

---

### Post by superprash2003 on 2009-07-28
if this is a laptop , make sure the wireless switch is set to ON ..
for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

