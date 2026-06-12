---
title: "Trouble connecting to Airport Extreme Base Station"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by woZa on 2007-09-13
Hi all. I am running 7.04 and am having issues with my airport extreme base station. I have a wireless card with the rt2561 chipset. I have followed [this]("http://ubuntuforums.org/showthread.php?t=296822&") howto to install the drivers from the ralink website (rather than the kernel module driver) and the card seems to be working ok (green light on).

```
ifconfig
```
```
eth0      Link encap:Ethernet  HWaddr 00:04:61:4F:E8:47  
          inet addr:10.0.1.10  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe4f:e847/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386355 (377.2 KiB)  TX bytes:402824 (393.3 KiB)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21072 (20.5 KiB)  TX bytes:21072 (20.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:08:A1:A7:7C:67  
          inet addr:10.0.1.11  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fea7:7c67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7481 errors:3 dropped:3 overruns:0 carrier:0
          collisions:10 txqueuelen:1000 
          RX bytes:1893268 (1.8 MiB)  TX bytes:9509 (9.2 KiB)
          Interrupt:19 
```

```
iwconfig
```
```
ra0       RT61 Wireless  ESSID:"USR9108"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Bit Rate=5.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level:-83 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
sudo iwlist ra0 scan
```
```
ra0       Scan completed :
          Cell 01 - Address: 00:14:7F:57:1C:4B
                    ESSID:"BTHomeHub-E488"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
          Cell 02 - Address: 00:13:49:A0:BA:EE
                    ESSID:"ZyXEL"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Quality:0/100  Signal level:-80 dBm  Noise level:-256 dBm
          Cell 03 - Address: 00:14:C1:04:C1:50
                    ESSID:"USR9108"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Quality:0/100  Signal level:-80 dBm  Noise level:-256 dBm
```

```
cat /etc/network/interfaces
```
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 10.0.1.10
        netmask 255.255.255.0
        gateway 10.0.1.1

iface ra0 inet static
        address 10.0.1.11
        netmask 255.255.255.0
        gateway 10.0.1.1
        auto ra0
```

Seems to be picking up base stations... But not mine! SSID of mine is Wireless.

There is no closed network or access control on the base station. I am a bit stumped now as to how to proceed. The fact that the wireless card can detect some networks (and seems to be connecting to USR9108 ) suggests that is ok and the base station is at fault but my powerbook with os x connects fine...

Any ideas anyone?

Thanks
Alex

---

### Post by woZa on 2007-09-13
A bit of an update...

```
sudo iwlist ra0 ap
```
```
ra0       Peers/Access-Points in range:
    00:14:7F:57:1C:4B : Quality:72/100  Signal level:-67 dBm  Noise level:-79 dBm
    00:11:24:98:61:F2 : Quality:94/100  Signal level:-45 dBm  Noise level:-79 dBm
    00:13:49:A0:BA:EE : Quality:54/100  Signal level:-85 dBm  Noise level:-79 dBm
```

00:11:24:98:61:F2 is the Airport ID of my base station but

```
sudo iwlist ra0 scan
```
Still doesn't pick it up, only the other two...

---

### Post by woZa on 2007-09-17
It seems that setting the basestation to choose  channel automatically prevents iwlist scan from picking it up. Now I have set the channel and can see the base station...

```
sudo ifup ra0
```
```
Listening on LPF/ra0/00:08:a1:a7:7c:67
Sending on   LPF/ra0/00:08:a1:a7:7c:67
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.0.0.2
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.2
bound to 10.0.0.7 -- renewal in 40215 seconds.
```

But still can't make any connections out...

Anyone???

---

### Post by woZa on 2007-09-18
Well thanks for your help everyone...!? managed to resolve my issues now so you can all go back to whatever it was you were doing before you showered me with offers of help.

---

