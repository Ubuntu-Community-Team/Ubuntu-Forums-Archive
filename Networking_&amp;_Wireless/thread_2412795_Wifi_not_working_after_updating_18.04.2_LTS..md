---
title: "Wifi not working after updating 18.04.2 LTS."
date: 2019-02-17
forum: Networking &amp; Wireless
---

### Post by khandekarv44 on 2019-02-17
After updating Ubuntu, my wifi is not working. 

Issues faced:
1. From top right corner menu, "Wifi off" is shown. And when i trey to turn it on, noting happens.  
2.  If i go to Wifi settings and turn on using the top orange colour button (which was off previously and was grey in colour. ), colour changes but it still says wifi is off. 
3. After closing and opening this dialog again, then it shows ON button. 
4. But below that is says "No wifi adaptor found. make sure you have wifi adaptor plugged and turned on".

Output of [COLOR=#242729][FONT=Consolas]lspci -knn | grep Net -A3

[/FONT][/COLOR]```
02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Kernel driver in use: wl
	Kernel modules: bcma, wl


```
Output of [COLOR=#333333][FONT=monospace]lshw -C network[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] 

[/FONT][/COLOR]```
[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]  *-network DISABLED        
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: e0:06:e6:d4:18:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f1900000-f1907fff
  *-network
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: 5c:f9:dd:3d:ea:c3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.35 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:f1800000-f183ffff ioport:2000(size=128)



```[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by praseodym on 2019-02-17
SecureBoot is turned off?

---

### Post by solisas on 2019-02-18
Try it with the  4.15.0-44 kernel. My wifi stopped after upgrading to 45 and worked again after going back to 44.

---

### Post by maramsumanth on 2019-02-18
[COLOR=#000000]Give the following command in terminal and check whether plugin is missing or not.

nmcli

Maybe you should see here [/COLOR]https://ubuntuforums.org/showthread.php?t=2412566, this was the same problem I faced, but still didn't solved.[COLOR=#000000]


[/COLOR]

---

