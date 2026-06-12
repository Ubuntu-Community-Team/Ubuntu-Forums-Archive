---
title: "WiFi Card Suddently Not working"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by ethernetdan on 2008-10-08
I am extremely new to Ubuntu and am having some problems with WiFi. About 2 months or so ago I ordered a new Dell TrueMobile 1350 MiniPCI wifi card and installed it on my Inspiron 5100 laptop. With some difficulty I configured Ndiswrapper. Until now everything has worked fine, Network Manager operated without a hitch and everything was great. Yesterday I turned on the computer and was unable to get WiFi. 
Here is the print out from various utilities
lshw -C network:
```
*-network: 1
description: Wireless interface
product: BCM4306 802.11 b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:02:02.0
logical name: wlan0
serial: :)
width: 32 bits
clock: 33 MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driver version=1.52+Broadcom,02/10/2005, 3.100. latency=32 link=no 
module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

iwlist wlan0 scan:
```
wlan0      No Scan Results
```

ifconfig:
```

wlan0      Link encap:Ethernet  HWaddr 00:0b:7d:0e:85:05
           UP BROADCAST MULTICAST  MTU:1500 Metric:1
           RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX Packers:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes: 0 (0.0 B)  TX bytes: 0 (0.0 B)
           Interrupt: 11  Memory: faffc000-faffe000
```

If I run ndiswrapper -m:
```
 module configureation contains directive install pci:[[Long string of numbers]] /sbin/modprobe ndiswrapper; you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MOD PROBE> Line 7.
```
It does that almost 15 times with a higher line number at the end each time.

Does anyone have any idea about what I should do next?

Thanks in Advance,
Daniel

---

### Post by ethernetdan on 2008-10-10
I have removed and purged ndiswrapper and reinstalled that and the driver and it still does not work. Does anyone have any tips?

---

### Post by Dre8927354 on 2008-10-11
I think you have the same problem as what I had every now and then with Hardy. This is what I did:

1.Go to Network Settings
2.Unlock 
3.Highlight Wireless connection and go to the Properties
4.Deselect “Enable roaming mode”
5.Type something in the “Network name” box
6.Under “Connection Settings”, change configuration to DHCP
7.Ok
8.It will show you a “Changing network setting dialogue”.
9.Redo 1-3
10.Select “Enable roaming mode”
11.Ok

If the connection works again then you might consider upgrading your Network Manager to version 0.7. It is explained in this thread: [http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059). I haven't had any problems after the upgrade.

---

