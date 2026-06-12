---
title: "Lubuntu 16.04 - no internet on the new ISP “Gateway/Cable modem/coax” connection"
date: 2017-06-02
forum: Networking &amp; Wireless
---

### Post by Xpdin on 2017-06-02
It is Lubuntu mini.iso with no desktop environment, only fvwm, so please, I can use only the terminal. I don't have any network manager installed.


There are two different routers:
On the sim router the wired internet connection works for the Lubuntu device. 


Immediately as I change the Ethernet cable from the above SIM router, to the other provider(router) which has only tv cable/coax connection through only a cable model(Gateway), there is no more internet connection.


With the same network cable/router port(from the second tv cable/coax/Gateway ISP)  the internet works on Windows 7 and 10.


From what I could see for the two different routers/connections the IPs are dynamically.


Tell me please what logs do you need from the working and no-working connections, in order to see the differences...


Thank you.

---

### Post by TheFu on 2017-06-02
**wicd-curses** is how I deal with wifi from the shell.

---

### Post by Xpdin on 2017-06-02
Thank you TheFu,

Sorry, I wasn't enough clear, I am only interested in the Ethernet connection.

regards.

Thank you for your replies...


Working internet connection:


```
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 68:f7:28:21:c8:85  
          inet addr:192.168.8.100  Bcast:192.168.8.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5842607 (5.8 MB)  TX bytes:1038943 (1.0 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:766404 (766.4 KB)  TX bytes:766404 (766.4 KB)


wlan0     Link encap:Ethernet  HWaddr ac:b5:7d:f2:ef:2f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


Non interet working connection(immediatelly after I only change the ethernet cable from a router to another)


```
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 68:f7:28:21:c8:85  
          inet addr:192.168.8.100  Bcast:192.168.8.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11441631 (11.4 MB)  TX bytes:2455373 (2.4 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:839056 (839.0 KB)  TX bytes:839056 (839.0 KB)


wlan0     Link encap:Ethernet  HWaddr ac:b5:7d:f2:ef:2f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


I am not interested in the WiFi connection.

There are two different routers:


One is connected to the internet through a sim card - one ISP (Linux has internet)
The second ISP is connected to the internet through a coaxial/tv cable/Gateway/Modem cable. (no internet on Linux for this one)


No configurations have been changed to any of the two routers or any machines Linux/Windows 7/Windows 10.


Only change the same cable for all the 3 difference devices from a router to another. Windows 10 and Windows 7 have internet connection on both routers.


Linux has internet only on the first SIM router.


Regards.

Regards.

---

### Post by TheFu on 2017-06-02
If you move the cable, you need to restart the networking subsystem. This isn't automatic on a minimal ubuntu setup.
Also, it is best to disable any wifi stuff.

I would check the **route** and dns settings if you do have connectivity to the router.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by Xpdin on 2017-06-02
For the non working internet connection to the link led from the router where is the Linux Ethernet cabled plugged, only the orange 
 led one blinks, but for the other internet working devices connected via Ethernet cable to the same router, blinks also the green led on the router.


Working internet connection:


```
~$ ping google.com
PING google.com (195.249.145.114) 56(84) bytes of data.
64 bytes from cache.google.com (195.249.145.114): icmp_seq=1 ttl=58 time=26.0 ms
64 bytes from cache.google.com (195.249.145.114): icmp_seq=2 ttl=58 time=35.6 ms
64 bytes from cache.google.com (195.249.145.114): icmp_seq=3 ttl=58 time=44.4 ms
64 bytes from cache.google.com (195.249.145.114): icmp_seq=4 ttl=58 time=43.2 ms
64 bytes from cache.google.com (195.249.145.114): icmp_seq=5 ttl=58 time=43.2 ms
64 bytes from cache.google.com (195.249.145.114): icmp_seq=6 ttl=58 time=39.4 ms
^C
--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5008ms
rtt min/avg/max/mdev = 26.059/38.670/44.463/6.378 ms




~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=48.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=57.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=56.1 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 48.494/54.102/57.670/4.023 ms



```


Non working internet connection for ping google.com after pending/waiting a few minutes, it appears:


```
~$ ping google.com
ping: unknown host google.com


~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.8.100 icmp_seq=1 Destination Host Unreachable
From 192.168.8.100 icmp_seq=2 Destination Host Unreachable
From 192.168.8.100 icmp_seq=3 Destination Host Unreachable
From 192.168.8.100 icmp_seq=4 Destination Host Unreachable
From 192.168.8.100 icmp_seq=5 Destination Host Unreachable
From 192.168.8.100 icmp_seq=6 Destination Host Unreachable
From 192.168.8.100 icmp_seq=7 Destination Host Unreachable
From 192.168.8.100 icmp_seq=8 Destination Host Unreachable
^C
--- 8.8.8.8 ping statistics ---
10 packets transmitted, 0 received, +8 errors, 100% packet loss, time 9026ms
pipe 3



```

Thank you TheFu,

When I moved the cable, before, I also tried for many times, restart the device, and the router also, no result yet...

---

### Post by TheFu on 2017-06-02
route?
restart the network subsystem?

---

### Post by Xpdin on 2017-06-02
I run ```
dhcpcd eth0
``` with the working internet cabled in, and after dhcpcd loaded everything, I plugged the cable in the non-working internet router, and the internet worked, maybe because dhcpcd was running.


I restarted the device to see if it will still work but when Linux loaded after restart it appeared in the  console:


```
Failed to start LSB: IPV4 DHCP client with IPV4ALL support.
See 'systemctl status dhcpcd.service' for details
16.780656 usb 1-1.4.3: device descriptor read/64, error -110
A start job is running to Raise network interfaces ( ** min **s / 5min 7s)
```


The last part "A start job is running..." where I have to wait 5 min and 7s it seams that appears every time that the internet doesn't work. It has never appeared when the internet worked, but it always appears when internet doesn't work...


After starting Linux with the non-working internet in, I also tried ```
dhcpcd eth0
``` but... ```
eth0: waiting for carrier
timed out
dhcpcd exited
```

And again...


I have just(nothing less or more) only moved the cable from the non-internet connection router to the internet working connection router 
```
dhcpcd eth0

```


Loaded all the things successfully(with the internet connection plugged) It is right that would not be a good idea to paste in here the output of "dhcpcd eht0" ?


Unplug the working internet connection and plug in to the non-internet connection, but surprise, now I am posting from the non-working internet connection which it seams that now is working because of the ```
dhcpcd eth0

```


But, if I will restart like last time, I think it will happen again like before


Regards.



Thank you.

As soon as "waiting for carrier" without touching anything else, I unplugged only the head on the network cable from the Linux machine, insert it in the Windows 7 machine, disable the wireless at all from the Windows machine, enable LAN, and internet is working... This could mean that the router/cable/port of the router work properly?


I will try also to reset the router...


Could it be any other configurations of Linux, considering that the internet works after I use ```
dhcpcd eth0
``` with the internet-working router plugged in, and after that, plugging in the non-internet router and still has internet connection... (until restart)

---

### Post by TheFu on 2017-06-02
route?
restart the network subsystem? 

I'm done. 3 times. No answer.

---

### Post by Xpdin on 2017-06-03
The only way the internet was working IN THE NON-INTERNET WORKING ROUTER (the same network cable/the same router port, everything the same like when it doesn't work) was ```
dhcpcd eht0
``` WHEN THE NETWORK CABLE WAS PLUGGED IN THE WORKING INTERNET ROUTER and after that only moving the cable from the working-internet-router to the non-working-internet router. 


But if I will restart the machine, no internet until I will not repeat the before steps.


I've also reset for a few times the router, restarted it (unplug from the electricity for at least 30 second) tried to reconnect the Linux machine to the non-internet-router with another cable router and also to another port router, but still not working, until I will not do the step from the beginning.


The same Ethernet cable and router port from the non-internet router provide internet instantly when is plugged into another Windows 7 and Windows 10 machines, without to change anything in Windows or in the fresh/new/from scratch reset router.


```
uname -a
Linux WindowsXP 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:29:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```


```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```


Here it is /var/log/dmesg
 
[https://paste.debian.net/hidden/8226e135/](https://paste.debian.net/hidden/8226e135/)

All the following commands are outputed with the internet working(connected to the usually non-internet router, until I will not do the steps from the beginning of this replay)

```
lshw -C network  *-network DISABLED      
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: ac:b5:7d:f2:ef:2f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-78-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:90500000-9057ffff memory:90580000-9058ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 68:f7:28:21:c8:85
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.110.11 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:88 ioport:1000(size=256) memory:90404000-90404fff memory:90400000-90403fff



```

```
more /etc/resolv.conf# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.8.1



```


```
route Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.110.1   0.0.0.0         UG    202    0        0 eth0
192.168.110.0   *               255.255.255.0   U     202    0        0 eth0



```

The var/log/kern.log it was to big to paste anywhere, and I don't know why I could not upload the file to any file hosting site, or on Google drive, or elsewhere. The file has only 2.1M. I've also tried to copy it/rename it, but it is not possible to upload it anywhere. even here on the forum as an File Attachment. Maybe because of the file content.


Sincerely,

Considering the before post, when I was connected on the internet through the regularly/usually non-working-internet router, but this time, before restart the internet was working on it(the reason for the working internet connection you can see at the beginning of the before post)

I only restarted the machine, without to touch anything else, router, cable or anything else.

Immediately after restart:

```
~$ ping google.com
ping: unknown host google.com

```

```
~$ ping 8.8.8.8
connect: Network is unreachable

```

```
~$ sudo dhcpcd eth0
[sudo] password for globalisation: 
eth0: waiting for carrier
timed out
dhcpcd exited

```

From the above post/replay it seams that 192.168.110.0 is the Gateway, It seams that it is right, because when I write in the browser it asks for the username and password of the modem/password

```
ping 192.168.110.1
connect: Network is unreachable
globalisation@WindowsXP:~$ ping 192.168.110.0
connect: Network is unreachable
globalisation@WindowsXP:~$ ping 192.168.8.1
connect: Network is unreachable
globalisation@WindowsXP:~$ ping 8.8.8.8
connect: Network is unreachable
globalisation@WindowsXP:~$ ping google.com
ping: unknown host google.com

```

```
:~$ dmesg |grep eth[0-9]
[    2.981426] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000768000, 68:f7:28:21:c8:85, XID 10900800 IRQ 88
[    2.981432] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   15.883064] r8169 0000:03:00.0 eth0: link down
[   15.883066] r8169 0000:03:00.0 eth0: link down

```
```
:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: ac:b5:7d:f2:ef:2f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-78-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:90500000-9057ffff memory:90580000-9058ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 68:f7:28:21:c8:85
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:88 ioport:1000(size=256) memory:90404000-90404fff memory:90400000-90403fff

```

```
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 68:f7:28:21:c8:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:130352 (130.3 KB)  TX bytes:130352 (130.3 KB)


wlan0     Link encap:Ethernet  HWaddr ac:b5:7d:f2:ef:2f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


```
:~$ more /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 208.67.222.222
nameserver 208.67.220.220



```

```
:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

Internet working connection on the regularly non-internet working router:


```
:~$ ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
```


No internet(because of restart) for the same above non-internet working router. There is no link detected, but  this same cable/machine/port had internet before restart...


```
:~$ ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
```


The always internet working router( completely another provider, another connections, another router)


```
:~$ ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```

---

### Post by Xpdin on 2017-06-03
It seams that these two commands resolve the problem:


```
sudo ethtool -s eth0 autoneg off speed 100 duplex full 
```
```
sudo dhcpcd eth0
```


Only that now, still have to find out how they could run on the system start, because after every restart the two commands should be used.


It seams that in adding them in /etc/rc.local doesn't have any effect.


Still at he boot there are these 3 issues:


```
[FAILED] Failed to start LSB: IPV4 DHCP client with IPV4LL support
[17.289877] usb 1-1.4.3: device descriptor read/64, error -110
A start job is running for Raise network interfaces (**min **s / 5min 8s)

```


And there is waiting time until the 5min 8s passes.
The last error it appears always only when the internet connection is not recognized, but never when the internet connection works from the beginning immediately after restart, without to use any commands in order to start the internet.

---

### Post by Xpdin on 2017-06-05
It seams that the final result, in order to have internet access automatically after reboot/shutdown/sleep with no more manual commands:


/etc/network/interfaces


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
iface eth0 inet dhcp
    pre-up ethtool -s eth0 autoneg off speed 100 duplex full


allow-hotplug eth0



```


/etc/rc.local


```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


echo 70 > /sys/class/backlight/intel_backlight/brightness
rfkill block bluetooth
rfkill block wifi
ethtool -s eth0 autoneg off speed 100 duplex full
ip link set eth0 up


exit 0

```

---

