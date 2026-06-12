---
title: "Getting wireless to work, (installed 11.04 over HP G62)"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by knutathon on 2011-07-06
Hello,

I realize there are many forum threads and other websites with similar questions to mine but I have not found anything to resolve my problems with getting wireless to work. 

I tried putting in 11.04 as a partition  to Windows 7 on my HP laptop a few weeks ago. Finding everything (including the wireless) was working to my satisfaction and being fed up with Windows I decided to re-install Ubuntu using the full hard disk space.

Now however, the button for enabling/disabling wireless on my keyboard (F12) is set to red and I cannot re-enable it. I've tried a few terminal commands mentioned in other threads  and this is my output. 
```

$ lspci -vnn | grep 14e4

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

``````

$ iwconfig

lo   no wireless extensions.

eth0   no wireless extensions

eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0
 
``````

$nm-tool

Device: eth1
Type 802.11 WiFi
Driver: wl
State: unavailable
Default: no
HW Address: 

Capabilities;

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encription: yes

``````

$lshw -C network
*-network DISABLED
 description: Wireless interface
product: BCM4313 802.11b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth1
version: 01
serial: 00:26:82:86:d9:78
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
resources: irq:17 memory:f0100000-f0103fff

``````

$rfkill list
0: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: yes

```

---

### Post by SpockVulcan on 2011-07-06
Is it listed under System > Administration > Additional Drivers?

---

### Post by fooman on 2011-07-06
try turning the wireless card off then on again via the terminal...see if that fixes it:

```
 ifconfig wlan0 down 
``````
 ifconfig wlan0 up
```replace *wlan0* with whatever your device is named (eth1 ?).

---

### Post by wildmanne39 on 2011-07-07
Hi, here is a link that should get your wireless working.Your card is the 4313 so follow the directions for it.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

