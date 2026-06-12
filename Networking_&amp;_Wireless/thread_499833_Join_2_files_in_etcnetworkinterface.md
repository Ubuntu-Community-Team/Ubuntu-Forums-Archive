---
title: "Join 2 files in etc/network/interface"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by shunklord on 2007-07-13
I have an ethernet card and a wifi card, I use the ethernet to connect to my modem and the wifi to connect outdoor, the problem is I can’t switch to Ethernet<->wifi without modify the file /etc/network/interfaces.


To use ethernet I have this :

```
auto lo
iface lo inet loopback
```
If I want wifi I put this
```
auto lo
iface lo inet loopback
iface eth0 inet dhcp
hwaddress ether 00:13:02:E4:48:70
```

I would like to only one file with this two files.

This results of ifconfig and iwconfig :

```
skd@xp2400:~$ ifconfig
ath0      Lien encap:Ethernet  HWaddr 00:19:5B:12:98:22
          adr inet6: fe80::219:5bff:fe3c:a8dd/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

eth0      Lien encap:Ethernet  HWaddr 00:E0:18:F3:D8:49  
          inet adr:192.168.0.128  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::2e0:18ff:fef3:d849/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2302011 erreurs:0 :0 overruns:0 frame:0
          TX packets:1410152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3262509626 (3.0 GiB) Octets transmis:81298397 (77.5 MiB)
          Interruption:18 Adresse de base:0x6000 

irda0     Lien encap:IrLAP  HWaddr 29:94:04:d7  
          UP RUNNING NOARP  MTU:2048  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:7588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:8 
          Octets reçus:0 (0.0 b) Octets transmis:114904 (112.2 KiB)

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:68 erreurs:0 :0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:5188 (5.0 KiB) Octets transmis:5188 (5.0 KiB)

wifi0     Lien encap:UNSPEC  HWaddr 00-19-5B-3C-A8-DD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:544 erreurs:0 :0 overruns:0 frame:172
          TX packets:266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:199 
          Octets reçus:62222 (60.7 KiB) Octets transmis:12236 (11.9 KiB)
          Interruption:19 

skd@xp2400:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:899  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.
```

Thanks for help

---

### Post by benjaminwr on 2007-07-13
Hi, im not exactly sure what you mean. Have you tried using the profiles in System > Administration > Network ?? Cheers

---

### Post by tturrisi on 2007-07-13
Your wired ethernet = eth0.
Your wifi = ath0.

Put all devices in /etc/network/interfaces UNLESS you have network-manager installed.  It would look like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback[

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

# Wireless interface
iface ath0 inet dhcp
hwaddress ether 00:19:5B:12:98:22   # this line not really necessary
auto ath0
```

---

