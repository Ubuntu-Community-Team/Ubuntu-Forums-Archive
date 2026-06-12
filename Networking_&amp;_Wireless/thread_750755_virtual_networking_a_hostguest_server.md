---
title: "virtual networking a host/guest server"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by deejmer on 2008-04-09
Hey good folks, I'm still catching on to networking on linux so need some help   :)  I'm probably doing something completely foolish, please don't laugh.  

I've installed an open source web control panel (ISPconfig.org) on a virtual instance of Ubuntu Server 7.10 using VirtualBox.  From my host machine, I'm trying to hit the front end for this control panel at 192.168.1.105:81/  (port 81 is the port the gui runs on) via a web browser .  

Needless to say...it doesn't work.

I've tried to include some (hopefully) relevant information.  

Host Machine: Ubuntu Desktop 7.10
Guest Machine: Ubuntu Server 7.10 (no GUI)

On the Network tab for the Guest Machine, I have Adapter 0 enabled, "Attached to: Host Interface" is selected, Cable connected is checked, and the Interface Name is vbox (as seen in my ifconfig below)

Here is my /etc/network/interfaces file on the **host** machine:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

#Aauto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp


#iface wlan0 inet dhcp
#wireless-essid HALO
#wireless-key EDAA41C90B077BCAB83029B9E9

#auto wlan0

```

Here is the ifconfig on my **host** machine:
```
eth0      Link encap:Ethernet  HWaddr 00:01:29:D7:76:A8  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed7:76a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14744200 (14.0 MB)  TX bytes:1273960 (1.2 MB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8600 (8.3 KB)  TX bytes:8600 (8.3 KB)

vbox      Link encap:Ethernet  HWaddr 00:FF:9A:40:DE:4A  
          inet6 addr: fe80::2ff:9aff:fe40:de4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

-----------------------------------------------

Here is my /etc/network/interfaces file on the **guest** machine:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth0
iface eth0 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

Here is the ifconfig on my **guest** machine:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:B5:B5:BD  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe76:b5bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10674 (10.4 KB)
          Interrupt:11 Base address:0xc020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14705 (14.3 KB)  TX bytes:14705 (14.3 KB)

```

Any help would be greatly appreciated.

Sorry for the long post.

Thanks!
[/code]

---

