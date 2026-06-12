---
title: "[SOLVED] Installed Wicd, USB adapter no longer recognized"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by tstack77 on 2008-07-26
I use a linksys wusb54gc usb wireless adapter. Nothing shows up when I plug it in anymore after installing wicd...wicd displays the Wireless interface as 'None'.

Any ideas?

---

### Post by imdano on 2008-07-26
Whats the output of
```
ifconfig -a
iwconfig
```

---

### Post by tstack77 on 2008-07-26
xxxxx@xxxxx:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:02:4d:a2:e3  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe4d:a2e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14610631 (13.9 MB)  TX bytes:2056161 (1.9 MB)
          Interrupt:11 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34600 (33.7 KB)  TX bytes:34600 (33.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:7f:6f:fc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-BF-7F-6F-FC-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

xxxxx@xxxxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by imdano on 2008-07-26
Is your wireless card plugged in?  It's not showing up in ifconfig -a, which means Ubuntu isn't detecting it properly (assuming its plugged in).  With the card plugged in, what's the output of ```
sudo lshw -C network
```

---

### Post by tstack77 on 2008-07-26
My fault, missed pasting the bottom part:

xxxxx@xxxxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



xxxxx@xxxxx:~$ sudo lshw -C network
[sudo] password for xxxxx: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:08:02:4d:a2:e3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.107 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:bf:7f:6f:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by tstack77 on 2008-07-26
I see that the usb card is detected in the terminal, but how do I get wicd to recognize the attached card/connect?

---

### Post by imdano on 2008-07-26
Open up the wicd preferences and put "wlan0" into the Wireless Interface text box.

---

### Post by tstack77 on 2008-07-26
Thank you! So simple of a fix but I would never have figured it out on my own...been spoiled by everything 'just working'

THANKS!!!

---

### Post by imdano on 2008-07-26
Yeah, typically wicd will be able to figure out what your wireless interface is on its own, but not in this case for some reason.  Maybe because when you initially installed wicd the card wasn't plugged in?  I'll see if I can tweak the detection scheme so that wicd will keep trying to detect a wireless interface if it doesn't find one on initial install.

---

