---
title: "Internet Connected but not detected?"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by jp.brandon on 2013-12-20
First off I am a new linux user and trying to switch my computers over to Ubuntu for developing. However on my work computer I have been having Internet problems. For the past 3 days I have been reading the forums and trying out different solutions with no success. Yesterday I seemed to fix the problem, but right after I rebooted the internet would not work anymore.

Here is the funny thing: When ever I start to write a thread for help, The internet starts to work again. I am pretty sure it is trolling me. However when i reboot the problem comes back.

Here are some details:

Ubuntu 13.10
Dual Booted with Windows 7

ping 8.8.8.8
```
brandon@brandon-Aspire-X1301:~$ sudo ifup eth0[sudo] password for brandon:
brandon@brandon-Aspire-X1301:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.3.1 icmp_seq=1 Destination Net Unreachable
From 192.168.3.1 icmp_seq=2 Destination Net Unreachable
From 192.168.3.1 icmp_seq=3 Destination Net Unreachable
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packetloss, time 2000ms
```

ifconfig -a
```
brandon@brandon-Aspire-X1301:~$ ifconfig -aeth0      Linkencap:Ethernet  HWaddr 00:26:2d:28:b0:ec  
          inetaddr:192.168.3.111 Bcast:192.168.3.255 Mask:255.255.255.0
          inet6 addr:fe80::226:2dff:fe28:b0ec/64 Scope:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Metric:1
          RXpackets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:1000
          RXbytes:21255 (21.2 KB)  TX bytes:10149(10.1 KB)
 
lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6 addr:::1/128 Scope:Host
          UP LOOPBACKRUNNING  MTU:65536  Metric:1
          RXpackets:167 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0txqueuelen:0
          RXbytes:13913 (13.9 KB)  TX bytes:13913(13.9 KB)
```

route -n
```
brandon@brandon-Aspire-X1301:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

cat /etc/network/interfaces
```
brandon@brandon-Aspire-X1301:~$ cat /etc/network/interfaces# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
 
# The primary network interface
#auto eth0
iface eth0 inet dhcp
```

nm-tool
```
brandon@brandon-Aspire-X1301:~$ nm-tool 
NetworkManager Tool
 
State: connected (global)
 
- Device: eth0-----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unmanaged
  Default:           no
  HW Address:        00:26:2D:28:B0:EC
 
  Capabilities:
    CarrierDetect:  yes
    Speed:           100 Mb/s
 
  Wired Properties
    Carrier:         on
```


What I am confused about that everytime I reboot it wont connect, but randomly like 20-40mins later it works. Any Ideas?

Thanks in advance.

---

### Post by Iowan on 2013-12-20
*/etc/network/interfaces* looks like it's set for a manual start (**#auto eth0**)
I doubt it's the problem, but you might comment out the **iface eth0 inet dhcp** line to see if Network Manager is happier.

---

### Post by jp.brandon on 2013-12-20
It did seem to help a bit, The network-manager says eth0 is connected. But when I try to ping 8.8.8.8 is still comes up with "Destination Net Unreachable"

---

### Post by Iowan on 2013-12-20
I presume 192.168.3.1 is your router, can you ping it?
Network Manager also has options to set routes. Check those.

---

