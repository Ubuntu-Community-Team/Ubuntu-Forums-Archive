---
title: "ubuntu edgy + D-Link Wireless USB Adapter"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by timvets on 2006-10-17
I have a ASRock - based Intel 2 Core Duo (or something) PC.
Ubuntu Edgy runs well, appart from some video card support issues.
(i810)
I plugged my D-Link "DWL-G122 802.11g/2.4GHz Wireless USB Adapter" in one of the USB ports.
I opened System>Administration>Networking
In the window "Network Settings" I see Two entries named
Wireless connection (wmaster0)
Wireless connection (wlan0)
when I unplug the D-Lin they both dissapear, so I guess they are both related to the same device.
I open the properties od one of them and start guessing what I should fill in:
Network name (ESSID) : TELENET HOTSPOT
Password Type : Plain (ASCII)
Network Password : <the password for getting on the wireless network here>

the rest I left as is

it doesn't work...
On Windoze XP I had a very effective little program named "Cirond Winc", which automatically detected newly found wireless networks to wich I could simply connect by right-clicking...I wish It were that easy on ubuntu.
:-?
can anyone help me with this please ?

thanks!

Tim

---

### Post by timvets on 2006-10-17
ok ik will put some outputs of commands  that might be related here, afaict


tim@timtop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8F:7B:E9:0F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:15:E9:B2:B2:C0  
          inet6 addr: fe80::215:e9ff:feb2:b2c0/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:35856 (35.0 KiB)
          Base address:0xf000 

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-B2-B2-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xf000 

tim@timtop:~$ cat /etc/resolv.conf
search telenet.be
nameserver 195.130.130.130
nameserver 195.130.129.162
tim@timtop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid TELENET HOTSPOT
wireless-key s:kunstz33


iface wmaster0 inet dhcp
wireless-essid TELENET HOTSPOT
wireless-key kunstz33

auto wmaster0


tim@timtop:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:15:E9:B2:B2:C0  
          inet6 addr: fe80::215:e9ff:feb2:b2c0/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:35136 (34.3 KiB)
          Base address:0xf000 

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-B2-B2-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xf000 





tim@timtop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:13:8f:7b:e9:0f
Sending on   LPF/eth0/00:13:8f:7b:e9:0f
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
^TDHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



tim@timtop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


thanks for any help!
Tim

---

