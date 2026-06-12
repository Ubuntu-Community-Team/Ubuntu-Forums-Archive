---
title: "rt2500 wireless card connection problem"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by ivek on 2005-07-16
I have installed drivers for rt2500 card (canyon wf511) on ubuntu 5.04 recently, following this howto:
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)

I have trouble connect to an access point dwl 2000+.
Maybe I should notice that I had no trouble establishing a connection with the same card and the same antenna under windows.

Here are some information about the configuration:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:00:F8:1F:AF:FE
          inet addr:192.168.16.2  Bcast:10.168.16.127  Mask:255.255.255.0
          inet6 addr: fe80::200:f8ff:fe1f:affe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1515 errors:3 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:180390 (176.1 KiB)  TX bytes:251834 (245.9 KiB)
          Interrupt:11 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2442831 (2.3 MiB)  TX bytes:2442831 (2.3 MiB)

ra0       Link encap:Ethernet  HWaddr 00:10:A7:2C:47:66
          inet addr:10.168.16.126  Bcast:10.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::210:a7ff:fe2c:4766/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3993 errors:2 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:185223 (180.8 KiB)
          Interrupt:10 Base address:0x8000

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"Staglisce"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=50/100  Signal level:-229 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:0F:3D:04:FD:98
                    Mode:Managed
                    ESSID:"Staglisce"
                    Encryption key:off
                    Channel:1
                    Quality:50/100  Signal level:-226 dBm  Noise level:-256 dBm

sit0      Interface doesn't support scanning.

```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.168.16.0     0.0.0.0         255.255.255.128 U     0      0        0 ra0
192.168.16.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.16.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         10.168.16.1     0.0.0.0         UG    0      0        0 ra0

```


When I try to ping AP adress i get:
```
 
PING 10.168.16.115 (10.168.16.115) 56(84) bytes of data.
From 10.168.16.126 icmp_seq=2 Destination Host Unreachable
From 10.168.16.126 icmp_seq=3 Destination Host Unreachable
From 10.168.16.126 icmp_seq=4 Destination Host Unreachable
From 10.168.16.126 icmp_seq=6 Destination Host Unreachable
From 10.168.16.126 icmp_seq=7 Destination Host Unreachable
From 10.168.16.126 icmp_seq=8 Destination Host Unreachable

--- 10.168.16.115 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6999ms
, pipe 3

```

I have managed to connect to this access point a few times, but in general it says "Destination Host Unreachable".
Can anyone tell what the problem is? 

Thanks!

---

### Post by rjeeves33 on 2005-07-18
hi mate

I apolgise if this if obvious based on the information you provided but do you get the same issue if you disable your eth0 adaptor?

Also does your AP have any WEP / WPA encryption enabled?  Are you using the RaLink Config Utility?  

Rob

---

### Post by skyboy on 2005-07-18
can you post also /etc/network/interfaces

could be a mapping trouble

---

### Post by halfpower on 2005-07-19
I'm new to all this Linux stuff but I've spent all together to much time trying to get my wireless card working using the Ubuntu 'How to.'   

I think the problem is that you are associating with your access point.  I have the same problem.  Thus far, I have not found a solution.

---

### Post by ivek on 2005-08-23
Hello again!
I've been away for some time...

> hi mate

I apolgise if this if obvious based on the information you provided but do you get the same issue if you disable your eth0 adaptor?

Also does your AP have any WEP / WPA encryption enabled? Are you using the RaLink Config Utility?

Rob

I get the same result if I disable eth0.

AP doesn't have wep, wpa or any encryption enabeled.
I'm not using ralink config. I've tried using wifi radar, but no results. :-(



> can you post also /etc/network/interfaces

could be a mapping trouble

This is what i get:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.16.2
        netmask 255.255.255.0
        network 10.168.16.0
        broadcast 10.168.16.127
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.168.4.2
        gateway 192.168.16.1


iface ra0 inet static
address 10.168.16.126
netmask 255.255.255.128
gateway 10.168.16.1
wireless-essid Staglisce





auto eth0

auto ra0

```

---

