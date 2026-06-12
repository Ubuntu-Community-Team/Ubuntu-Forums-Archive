---
title: "Ethernet not getting IP from DHCP Server, Wifi is"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by demslam on 2014-09-28
Hello All, 
Wanted to know if someone would be able to help me.
I wanted to change my ethernet from static to dynamic
so i change my /etc/network/interfaces to
auto eth0
iface eth0 inet dhcp

but it is not getting a ip from my router.
```
dem@streambox:~$ sudo ifdown eth0
```
```
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:01:2e:40:95:98
Sending on   LPF/eth0/00:01:2e:40:95:98
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.231 port 67 (xid=0xc6a378e)

```

```
dem@streambox:~$ sudo ifup eth0
```
```
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:01:2e:40:95:98
Sending on   LPF/eth0/00:01:2e:40:95:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0x77223a48)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 (xid=0x77223a48)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```




I also changed the wireless to get a dynamic ip as well
auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant/mnn.conf 

```
dem@streambox:~$ sudo ifdown wlan0
```
```
[sudo] password for dem:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/74:2f:68:e0:fd:6a
Sending on   LPF/wlan0/74:2f:68:e0:fd:6a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67 (xid=0x6eb9148a)
```
```
dem@streambox:~$ sudo ifup wlan0
```
```
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/74:2f:68:e0:fd:6a
Sending on   LPF/wlan0/74:2f:68:e0:fd:6a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x52138459)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x52138459)
DHCPREQUEST of 192.168.1.34 on wlan0 to 255.255.255.255 port 67 (xid=0x52138459)
DHCPOFFER of 192.168.1.34 from 192.168.1.1
DHCPACK of 192.168.1.34 from 192.168.1.1
bound to 192.168.1.34 -- renewal in 36677 seconds.
```

I am not sure why the ethernet is releasing to 192.168.1.231 and the wifi is releasing to 192.168.1.1. Any insight would be greatly appreciated.
Thank you

---

