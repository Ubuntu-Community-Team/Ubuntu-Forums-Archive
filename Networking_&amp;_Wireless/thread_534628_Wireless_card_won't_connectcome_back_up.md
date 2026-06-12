---
title: "Wireless card won't connect/come back up"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by ah_skeet on 2007-08-25
I have a Netgear WG311v3, which I used ndiswrapper to install, and it has been working fine for over a year now. 

Yesterday, the connection seemed to be going a little slowly, so I tried to run ```
/etc/init.d/networking restart
``` which has helped and worked before. But this time, the wireless card wouldn't reconnect to the router. 

```
iwlist wlan0 scanning
``` works fine, and the ethernet port works fine, but the wireless card won't connect to anything. 

I don't think it's a router issue, since the laptop I'm on connects to it fine, and it won't connect to other routers around. Restart the computer didn't even help.

Here are some outputs of various commands. Not sure how useful they'll be.

iwconfig
```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm
          RTS thr=2346 B   Fragment thr=2346 B
          Encryption key:0000-0000-00   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

/etc/init.d/networking restart
```
Listening on LPF/wlan0/00:14:6c:33:2b:d7
Sending on   LPF/wlan0/00:14:6c:33:2b:d7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

lshw -C network
```
  *-network:0
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:33:2b:d7
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=NETGEAR,02/22/2005,3.1.1.7 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fdee0000-fdeeffff iomemory:fded0000-fdedffff irq:20
```

iwevent  during networking restart
```
12:46:35.085158   wlan0    Set Encryption key:off
12:46:35.103224   wlan0    Set ESSID:off/any
12:46:39.160733   wlan0    Set Encryption key:****-****-**
12:46:39.168301   wlan0    Set ESSID:"143"
```

Any ideas?

---

