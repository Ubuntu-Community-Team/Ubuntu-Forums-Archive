---
title: "Toshiba Satellite Atheros WiFi not Working"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by graphicw on 2007-06-29
I have a Toshiba Satellite with an Atheros mini-PCI wireless card,  It is not able to connect to the network even though Network Manager shows the network SSID and encryption type.  I have tied WPA2, WPA (TKIP), WEP and no encryption and no matter what, I cannot succeed in getting an IP on the network.  I tried to set an IP and that failed as well even though the network manager then showed me as being connected.  I checked the router IP table and could not see my Toshiba Satellite on the network.

Does anybody have any pointers for me?  Thanks!

---

### Post by graphicw on 2007-06-29
Here is what iwconfig shows me:


```
graphicw@gwmobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:1639316  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by graphicw on 2007-06-29
```

graphicw@gwmobile:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:f5:44:3f:fe
Sending on   LPF/ath0/00:11:f5:44:3f:fe
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by graphicw on 2007-06-29
```

02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (
rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7064
        Flags: bus master, medium devsel, latency 168, IRQ 23
        Memory at e0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

---

