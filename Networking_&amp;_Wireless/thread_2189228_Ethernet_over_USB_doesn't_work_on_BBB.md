---
title: "Ethernet over USB doesn't work on BBB"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by rogi2 on 2013-11-21
Hi!

I've recently installed Ubuntu 13.04 on the Beagle Bone Black. This image: 

```
https://rcn-ee.net/deb/flasher/raring/BBB-eMMC-flasher-ubuntu-13.04-2013-10-08.img.xz
```

This microcontroller allows to share internet connection between host PC (Version 12.04 (precise) (64-Bit), Kernel Linux 3.2.0-56-generic) and BeagleBone over USB, so I went for it and configured the device as follows:

BeagleBone Black:
```
ifconfig usb0 192.168.7.2
route add default gw 192.168.7.1

```

Host PC:
```
sudo su
#eth0 is my internet facing interface, eth3 is the BeagleBone USB connection
ifconfig eth2 192.168.7.1
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth2 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
```

After that Internet Connection works itself, when I do ```
ping 8.8.8.8
``` I get the results:

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=47 time=4.63 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=47 time=4.68 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=47 time=4.57 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=47 time=4.58 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 4.578/4.620/4.682/0.063 ms
```

To have DNS configured too I typed aswell ```
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
``` but unfortunately when I do ```
ping google.com
``` I get, after few seconds of computing, ```
ping: unknown host google.com
```

So - I know, that this solution isn't good, but for this session it could work and it doesn't. What's more, both - BBB and PC - use resolvconf. To be honest I've got no clue how to configure network using this program... I tried changing ```
/etc/network/interfaces
``` on Beagle Bone Black like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp
# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE

# WiFi Example
#auto wlan0
#iface wlan0 inet dhcp
#    wpa-ssid "essid"
#    wpa-psk  "password"

# Ethernet/RNDIS gadget (g_ether)
# ... or on host side, usbnet and random hwaddr
# Note on some boards, usb0 is automaticly setup with an init script
# in that case, to completely disable remove file [run_boot-scripts] from the boot partition
auto usb0
iface usb0 inet static
    address 192.168.7.2
    netmask 255.255.252.0
    network 192.168.7.0
#broadcast 192.168.7.3
    gateway 192.168.7.1
    dns-nameservers 8.8.8.8 8.8.4.4


```

but it didn't help.

I don't know what else should I do. Please help.

Additional useful infos:

Beagle Bone Black:
ifconfig
```


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

usb0      Link encap:Ethernet  HWaddr ce:39:f3:4a:c7:94  
          inet addr:192.168.7.2  Bcast:192.168.7.3  Mask:255.255.255.252
          inet6 addr: fe80::cc39:f3ff:fe4a:c794/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57484 (57.4 KB)  TX bytes:63078 (63.0 KB)


```

route
```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.7.1     0.0.0.0         UG    0      0        0 usb0
192.168.7.0     *               255.255.255.252 U     0      0        0 usb0


```

uname -a
```


Linux arm 3.8.13-bone28 #1 SMP Fri Sep 13 03:12:24 UTC 2013 armv7l armv7l armv7l GNU/Linux


```

/etc/resolv.conf
```


nameserver 8.8.8.8
nameserver 8.8.4.4
#domain localdomain
#search localdomain
#nameserver 192.168.1.1


```

PC:

ifconfig
```
eth0      Link encap:Ethernet  Hardware Adresse 00:17:31:8d:6a:a6  
          inet Adresse:141.3.81.154  Bcast:141.3.83.255  Maske:255.255.252.0
          inet6-Adresse: fe80::217:31ff:fe8d:6aa6/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:30732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5888 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:7266589 (7.2 MB)  TX-Bytes:1286462 (1.2 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  Hardware Adresse 00:04:75:ca:98:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)
          Interrupt:21 Basisadresse:0xe400 

eth2      Link encap:Ethernet  Hardware Adresse c8:a0:30:ac:2c:95  
          inet Adresse:192.168.7.1  Bcast:192.168.7.3  Maske:255.255.255.252
          inet6-Adresse: fe80::caa0:30ff:feac:2c95/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:637 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:45704 (45.7 KB)  TX-Bytes:88161 (88.1 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:840 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:142988 (142.9 KB)  TX-Bytes:142988 (142.9 KB)


```

route
```


Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         i60-gw-int.ipr. 0.0.0.0         UG    0      0        0 eth0
141.3.80.0      *               255.255.252.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth2
192.168.7.0     *               255.255.255.252 U     1      0        0 eth2


```

uname -a
```


Linux i60p354 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 09:20:45 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```

What can be important - PC, which share Internet with BBB works in the University network, which is far more complicated than normal home network - could that cause problems with DNS resolving?

I'll be very thankful for your reply!

Best regards

---

### Post by Iowan on 2013-11-21
The "ping 8.8.8.8' success was from the BBB?
Sounds like the Ethernet over USB  works fine on the BBB.
The connection sharing... ???

---

### Post by rogi2 on 2013-11-21
Yep, I was pinging from BBB. I can actually ping anything from BBB but only when the IP adress is given instead of domain. I need the internet only to install some packages on BBB.

What do you mean by connection sharing?

---

### Post by Iowan on 2013-11-21
> **rogi2 said:**
> What do you mean by connection sharing?Years ago, there was a How-To on Internet Connection Sharing. Sounds like the connection is working, though (just not the DNS). I'd ask about connecting the BBB directly to the network, but doubt that'd be kosher.

---

### Post by rogi2 on 2013-11-21
I cannot afford connecting BBB with eth cable, so this solutions falls off. Any other ideas how to repair DNS settings?

---

