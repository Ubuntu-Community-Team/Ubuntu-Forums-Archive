---
title: "Assistance needed for multiple NIC setup"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by gene02 on 2007-07-15
Hello.  I'm having some trouble with my networking setup that I just can't solve.  I'm hoping someone can notice what I'm doing wrong.

I've been running a server setup with 2 NIC cards, one pointed to the internet and the other my home network.  I've just swapped in a pair of new ethernet cards to replace the built in interface and older PCI card that I've been using.  Unfortunately, I can't get the new setup working.  For the moment, I have the built in ethernet (eth1) connected to the internet and was trying to get the new PCI-X ethernet card (eth2) working with the LAN.  However, when I bring eth2 online, I can no longer get out through eth1.

Here are some details:
```
>ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:18:8B:72:DA:1C  
          inet addr:66.92.15.192  Bcast:66.92.15.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe72:da1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11067734 (10.5 MiB)  TX bytes:19650922 (18.7 MiB)
          Interrupt:19 

eth2      Link encap:Ethernet  HWaddr 00:E0:4C:0A:C9:7E  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:678 (678.0 b)  TX bytes:13049 (12.7 KiB)
          Interrupt:17 Base address:0x6000 

eth3      Link encap:Ethernet  HWaddr 00:0A:CD:13:6B:9E  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23878861 (22.7 MiB)  TX bytes:23878861 (22.7 MiB)

> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.92.15.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         66.92.15.1      0.0.0.0         UG    0      0        0 eth1

> cat /etc/network/interfaces
iface eth1 inet static
address 66.92.15.192
netmask 255.255.255.0
gateway 66.92.15.1
auto eth1

iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1
auto eth2

iface eth3 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.2
#auto eth3
```

The configuration above is working when only eth1 is up.  When I bring eth2 up, I can no longer get out through eth1.  The eth3 configuration is temporary as that will replace eth1 once I figure out how to get these things working again.

This is what the routing table looks like when I bring eth2 up:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
66.92.15.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
0.0.0.0         66.92.15.1      0.0.0.0         UG    0      0        0 eth1
```

Thanks for your input.
Gene

---

### Post by Mr. C. on 2007-07-15
There are two default routes in your routing table:
```

0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
0.0.0.0         66.92.15.1      0.0.0.0         UG    0      0        0 eth1
```

Remove the one that does not lead to your router / internet:

route del default gw 192.168.0.1

or

route del default gw 66.92.15.1

See also my post: 
[http://ubuntuforums.org/showthread.php?t=397576&highlight=default+route+%2Fetc%2Fnetwork%2Finterfaces](http://ubuntuforums.org/showthread.php?t=397576&highlight=default+route+%2Fetc%2Fnetwork%2Finterfaces)

MrC

---

### Post by gene02 on 2007-07-15
Thanks for the reply.  You were right, removing the second default gateway allows the first interface to keep working.  The second interface still isn't working though.  This was the same setup I was using with the old ethernet cards so I'm not sure why it's not working now.  How do I configure /etc/network/interfaces for the internal LAN interface?
```

> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
66.92.15.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         66.92.15.1      0.0.0.0         UG    0      0        0 eth0

> cat /etc/network/interfaces
auto lo
iface lo inet loopback

# eth0 = internet (builtin nic)
# eth1 = lan

auto eth0
iface eth0 inet static
        address 66.92.15.192
        netmask 255.255.255.0
        gateway 66.92.15.1

auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
```

(I switched eth1 and eth2 to eth0 and eth1 from how it was shown in my previous posting).

Thanks,
Gene

---

### Post by Mr. C. on 2007-07-15
Whenever you make changes, please post the updated output that shows how the system is configured.  I need to see:

```
ifconfig -a
```

Where is your loopback network route ?  eg:

```
127.0.0.0       0.0.0.0         255.0.0.0       U         0 0          0 lo
```

When you say the second interfaces aren't working, what do yo mean?  What are the IP addresses of the other stations connected to eth1 ?  Can you ping any of them ?  Can they ping 192.168.0.1 ?

MrC

---

### Post by gene02 on 2007-07-15
Here's the ifconfig -a.  Note that eth2 is not being used at the moment.

```
> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:8B:72:DA:1C  
          inet addr:66.92.15.192  Bcast:66.92.15.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe72:da1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4567778 (4.3 MiB)  TX bytes:11949706 (11.3 MiB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:0A:C9:7E  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:0A:CD:13:6B:9E  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2367933 (2.2 MiB)  TX bytes:2367933 (2.2 MiB)

```


I can't ping anything on the internal network, e.g. 192.168.0.4, and they can't ping this machine.
Here are the ping results:

```

> ping 192.168.0.4
PING 192.168.0.4 (192.168.0.4) 56(84) bytes of data.

--- 192.168.0.4 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9007ms

> ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.066 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.061 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.060 ms

```


When I had eth0 set up as 192.168.0.1 and that interface connected to the internal network, that worked fine, I could see the other internal machines.  Once I set eth0 to the external network, and eth1 to the internal network, I couldn't see anything in the LAN anymore

---

### Post by Mr. C. on 2007-07-15
```

eth0      Link encap:Ethernet  HWaddr 00:18:8B:72:DA:1C  
          inet addr:66.92.15.192  Bcast:66.92.15.255  Mask:255.255.255.0
          **UP** BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
eth1      Link encap:Ethernet  HWaddr 00:E0:4C:0A:C9:7E  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
```

Note that your eth1 is not configured as UP.

```
ifconfig eth1 up
```

Will enable it.  After that, you'll be able to ping the other stations on the LAN.

MrC

---

### Post by gene02 on 2007-07-15
You're right.  But that was only an oversight while I was messing around with it.  I've brought it back up and still no go.  Here are ifconfig and route again:

```
>ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:8B:72:DA:1C  
          inet addr:66.92.15.192  Bcast:66.92.15.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe72:da1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11548543 (11.0 MiB)  TX bytes:24705939 (23.5 MiB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:0A:C9:7E  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:546 (546.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:0A:CD:13:6B:9E  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9564346 (9.1 MiB)  TX bytes:9564346 (9.1 MiB)

> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
66.92.15.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         66.92.15.1      0.0.0.0         UG    0      0        0 eth0

> ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.

--- 192.168.0.2 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5008ms


```

I did just notice this in syslog:

```

Jul 15 15:30:08 howler kernel: [15642.929027] r8169: eth1: link down
Jul 15 15:30:08 howler kernel: [15642.964836] r8169: eth1: link down
Jul 15 15:30:18 howler kernel: [15652.910637] r8169: eth1: link down
Jul 15 15:30:18 howler kernel: [15652.947306] r8169: eth1: link down
Jul 15 15:30:28 howler kernel: [15662.892394] r8169: eth1: link down
Jul 15 15:30:28 howler kernel: [15662.929679] r8169: eth1: link down

```

---

### Post by Mr. C. on 2007-07-15
I believe Network Manager is interfering.  If you have eth1 set to **auto** in /etc/network/interfaces, Network Manager will continually configure the interface as specified.  Remove the auto declaration.

MrC

---

### Post by gene02 on 2007-07-16
Mr. C, it looks like that fixed it!  Thanks for your help.

However, I don't understand why the 'auto' declaration is breaking things, particularly since that is how it had been configured for the previous working setup.

---

### Post by Mr. C. on 2007-07-16
The "auto" declaration tells network manager to automatically configure this interface.  It is constantly running, and pulls the rug out from under you.  The Network Manager interface is not currently designed very well to help users manage multi-homed systems.

MrC

---

