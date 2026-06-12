---
title: "Network seems to have broken with linux..."
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by MJBoa on 2008-06-25
My network seems to not function well with Linux for some reason. The weird thing is that it was working pretty well for a while. I had ubuntu installed and the internet was working perfectly but one day it started acting up. I'll use network manager to connect to my network and I'll be connected for like 10-20 seconds then all of a sudden it won't connect to anything. Then it will come back and then it will disconnect. I don't know what the problem could be seeing as I reinstalled linux multiple times, the same thing happens with the Live CD and I've tried anything I could think of. I don't see how something I did on one installation could affect the Live CD. But it WAS working perfectly before.
Everything is fine on Windows. My only explanation is that either the network adapter, DWL G122 or the router, WRT54G don't like Ubuntu all of a sudden. Any suggestions on either a new adapter I could buy that I can use easily and functions fully under Linux or something I could fix?

---

### Post by earthmeLon on 2008-06-25
What do you get if you do:
```
ifconfig
```

---

### Post by MJBoa on 2008-06-25
ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:13:46:e5:5e:18  
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-E5-5E-18-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


iwconfig
```
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:2B:6D:71   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=31/100  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsusb
```
Bus 002 Device 003: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05fe:1011 Chic Technology Corp. 
Bus 001 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 001: ID 0000:0000
```

/etc/network/interfaces
```
iface wlan0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk random
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid linksys
auto wlan0
```

---

### Post by superprash2003 on 2008-06-25
type ping google.com in your terminal and post output

---

### Post by mempman on 2008-06-25
> **MJBoa said:**
> ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:13:46:e5:5e:18  
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  **MTU:1500**  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

This is a rather strange problem; some routers don't work well with linux w/ MTU size set at 1500.  Try to change that value in your router to something like 1370 and see if the same problem arises.

---

### Post by MJBoa on 2008-06-26
Not on Linux now but it says Destination Host Unreachable.

---

### Post by MJBoa on 2008-06-26
By the way, I'm open to buying a new wireless card, one that works completely.

---

### Post by earthmeLon on 2008-06-26
Get something with Atheros chipset :D

---

