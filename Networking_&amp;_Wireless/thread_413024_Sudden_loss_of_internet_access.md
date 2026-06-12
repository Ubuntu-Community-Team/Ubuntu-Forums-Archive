---
title: "Sudden loss of internet access"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by quix0te on 2007-04-18
I recently installed Ubuntu on my laptop.  The internal wireless card wasn't recognized, and I didn't yet feel like messing with ndiswrapper, so I plugged in a D-Link AirPlus DWL-G650 PCMIA card and it worked fine from the start.  Yesterday while working, however, I suddenly lost internet access.  The network configuration tool says that it's still connected, and I can browse files on the network share, but that's it.  I can't even go to the router's page at 192.168.0.1 in my browser.


The network configuration tool shows this:
```
Connection Properties: ath0

Internet Protocol (IPv4)
Address:	192.168.0.104
Broadcast:	192.168.0.255
Subnet Mask: 255.255.255.0

Network Device
Type:	Ethernet
Address: 00:0D:88:58:F2:BD

```

iwconfig returns this:
```
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"CUMMINGS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:BF:2C:C7   
          Bit Rate:18 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
          Rx invalid nwid:161594  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```


After trying "sudo dhclient ath0," the system log shows this:
```
Apr 18 17:33:21 colton-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Apr 18 17:33:21 colton-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Apr 18 17:33:21 colton-laptop dhclient: All rights reserved.
Apr 18 17:33:21 colton-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 18 17:33:21 colton-laptop dhclient: 
Apr 18 17:33:21 colton-laptop dhclient: wifi0: unknown hardware address type 801
Apr 18 17:33:22 colton-laptop dhclient: wifi0: unknown hardware address type 801
Apr 18 17:33:22 colton-laptop dhclient: Listening on LPF/ath0/00:0d:88:58:f2:bd
Apr 18 17:33:22 colton-laptop dhclient: Sending on   LPF/ath0/00:0d:88:58:f2:bd
Apr 18 17:33:22 colton-laptop dhclient: Sending on   Socket/fallback
Apr 18 17:33:22 colton-laptop dhclient: DHCPREQUEST on ath0 to 255.255.255.255 port 67
Apr 18 17:33:22 colton-laptop dhclient: DHCPACK from 192.168.0.1
Apr 18 17:33:22 colton-laptop dhclient: bound to 192.168.0.104 -- renewal in 279778 seconds.
Apr 18 17:34:42 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 18 17:34:42 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:34:45 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 18 17:34:45 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:34:51 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr 18 17:34:51 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:35:05 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Apr 18 17:35:05 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:35:22 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 18 17:35:22 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:35:32 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 18 17:35:32 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:35:42 colton-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Apr 18 17:35:42 colton-laptop dhclient: send_packet: Network is down
Apr 18 17:35:43 colton-laptop dhclient: No DHCPOFFERS received.
Apr 18 17:35:43 colton-laptop dhclient: No working leases in persistent database - sleeping.

```


I have no idea what's going on.

---

### Post by Compyx on 2007-04-18
Have you tried resetting your router?

---

### Post by quix0te on 2007-04-18
> **Compyx said:**
> Have you tried resetting your router?

Huh... I just cycled the modem and reset the router, and now it works.  Weird.. the other computers on the network (running Windows) had no problems.

Thanks much.

---

### Post by quix0te on 2007-04-21
Of course, today it's happened for the fourth time, and my dad is getting mad at me for resetting the router/modem so much.  I'd call comcast, but I doubt that'd be productive.

---

### Post by talon95 on 2007-04-22
I've got the same problem here.  It seems to die after a period of time with heavy network traffic.  I tried re-starting the connection through the GUI, but no luck.  Restarting my modem/router did not work either.  

Anyone have any other suggestions of things to try?  Thanks.

---

### Post by quix0te on 2007-04-22
Can you post, talon, some of the information I did from iwconfig and the syslog?  To tell you the truth, I don't really know what I'm doing, but I'm trying to learn as much as I can.

---

### Post by talon95 on 2007-04-22
I'm planning to, but haven't had time to work on it again this morning.  I did do some digging and suspect it's the sky2 driver as it's been problem prone according to these threads.

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68338](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68338)

[http://ubuntuforums.org/showthread.php?t=365385&highlight=yukon](http://ubuntuforums.org/showthread.php?t=365385&highlight=yukon)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009)

What motherboard/NIC do you have?  I've got the Giga DS3, which is one of the problem boards.

I'll post more later when I have time.

---

### Post by talon95 on 2007-04-28
The fix at the bottom of this page worked for me (installing Marvell driver).

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009)

---

