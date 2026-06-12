---
title: "wlan0 inop due to RF-kill"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by bug67 on 2014-03-22
I am having trouble with my wireless on an Asus X551C.

From Terminal:

"lshw -class network" returns:
```
*-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 24:0a:64:bf:ce:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-18-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff

```

"ifconfig wlan0 up" returns:
```
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

"rfkill list returns":
```
0: phy0: Wireless LAN
	Soft blocked: no
	**Hard blocked: yes**
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

So, I cannot seem to figure out how to remove the hard block from wlan0.  The physical switch (it's a keyboard button on the f2 key) has no affect.  

"rfkill unblock all" does nothing.

Any help would be greatly appreciated.  This machine was a Christmas gift for my fience.  It had Windows 8 on it and we got nowhere.  She asked me to install Linux on it.  Having done so, everything is perfect...except for this wifi issue.  Thanks in advance.

---

### Post by bug67 on 2014-03-22
Found the answer!

[http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

---

