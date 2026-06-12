---
title: "Ubuntu 16.04 detects enp2s0 but not eth0"
date: 2017-05-04
forum: Networking &amp; Wireless
---

### Post by mclaren2 on 2017-05-04
Hello, using 16.04 LTS, also new to Ubuntu.
My problem is that my ethernet cable is being detected (as enp2s0) but eth0 never shows up. I have an AR8161 Ethernet controller, and using wifi on the same router, it works fine (on a laptop with Ubuntu)

I did a fresh install of Ubuntu and doing: ifconfig -a  gives this output:

```
enp2s0  Link encap:Ethernet HWaddr 40:8d:5c:c3:9c:be
                        inet6 addr: fe80::ab1c:c176:e709:bc6d/64 Scope:Link
                        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
                        RX packets:28 errors:0 dropped:0 overrunrs:0 carrier:0
                        collisions:0 txqueuelen:1000
            .. .. 
 
            lo          Link encap:Local Loopback
                         inet addr:127.0.0.1 Mask:255.0.0.0
                         UP LOOPBACK RUNNING MTU:65536 Metric:1
                         
                         ... 
```

And doing 
```
sudo lshw -C network
``` gives the output:

```
*-network
                   description: Ethernet interface
                   product: AR8161 Gigabit Ethernet
                   vendor: Qualcomm Atheros
                   physical id: 0
                   bus info: pci@0000:02:00.0
                   logical name: enp2s0
                   version: 10
                   serial: 40:8d:5c:c3:9c:be
                   ....
                  configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port= twisted pair
```

When I connect the ethernet cable to the laptop, it still doesn't work. But the wi-fi works.

Any ideas?

---

### Post by TheFu on 2017-05-04
16.04 switched to a new udev with the systemd take-over.  Network device names have changed, for good.
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) explains how it works now.

If the naming isn't the only issue, please perform some simple troubleshooting with only 1 network interface enabled that you want to get working. DO NOT HAVE both wifi and wired ethernet connected at the same time.

---

### Post by mclaren2 on 2017-05-04
Oh, okay. So enp2s0 replaced that. I looked at older posts, so that's why.

I've done pretty much everything though (in my capability) and it still doesn't connect to the internet correctly. 
 I have:
Changed the MTU
Installed drivers for the ethernet controller
Changed the interface file

and much more stuff I can't recall. Yet it just recognizes it and then disconnects and goes offline.

---

### Post by TheFu on 2017-05-04
Please show your work.  Post the interfaces file first. Then ping the router by IP, then ping 8.8.8.8, then ping google.com.  In that order, until one of them fails. Show all your work - command AND output.  Please use **code tags** so things line up. Don't interpret, don't edit the output.

**sudo lshw -C network** would help too.

---

### Post by jeremy31 on 2017-05-04
Have you tried setting the MTU to 9000 for the Atheros?  I believe this bug was still present in the 4.4 kernel [https://bugzilla.kernel.org/show_bug.cgi?id=70761](https://bugzilla.kernel.org/show_bug.cgi?id=70761)

---

### Post by mclaren2 on 2017-05-04
Yes, I did try setting it to 8192, no result.

```
**sudo lshw -C network** *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 40:8d:5c:c3:9c:be
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:27 memory:fdcc0000-fdcfffff ioport:df00(size=128)



```

Interface file:
```


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
allow-hotplug enp2s0
iface enp2s0 inet dhcp



```
```

ifconfig -a
enp2s0    Link encap:Ethernet  HWaddr 40:8d:5c:c3:9c:be  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5528 (5.5 KB)  TX bytes:20614 (20.6 KB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1352 (1.3 KB)  TX bytes:1352 (1.3 KB)

```

Pings:
```
ping 8.8.8.8connect: Network is unreachable

ping google.com
ping: unknown host google.com

ping 192.168.1.3
connect: Network is unreachable



```

---

### Post by TheFu on 2017-05-04
Add 
**auto enp2s0**
to the interfaces file. I've never used hotplug.

The pings are in reverse order. I doubt that 192.168.1.3 is the router IP.  It could be 192.168.1.1 or 192.168.0.1 or something else.  .3 would be very odd, so please prove this from some other device that is working.  The other pings are useless if the router can't be pinged, right?

As for MTU, try a lower value. There is overhead that some network devices cannot handle. There are network devices that don't understand jumbo frames and some don't understand non-standard jumbo frames either.  Did this ever work with any other devices or releases?

---

### Post by mclaren2 on 2017-05-04
okay, i checked the local IP and it was indeed 192.168.1.1. My apologies. Here is the output:

```
ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.10.181 icmp_seq=1 Destination Host Unreachable
From 169.254.10.181 icmp_seq=2 Destination Host Unreachable
From 169.254.10.181 icmp_seq=3 Destination Host Unreachable
.
.
From 169.254.10.181 icmp_seq=53 Destination Host Unreachable
From 169.254.10.181 icmp_seq=54 Destination Host Unreachable


^C
--- 192.168.1.1 ping statistics ---
57 packets transmitted, 0 received, +54 errors, 100% packet loss, time 57328ms
pipe 4



```

I did ifconfig again, and look at the output:

```
ifconfig -a

enp2s0    Link encap:Ethernet  HWaddr 40:8d:5c:c3:9c:be            inet6 addr: fe80::428d:5cff:fec3:9cbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1246 (1.2 KB)  TX bytes:14938 (14.9 KB)
          Interrupt:18 


enp2s0:avahi Link encap:Ethernet  HWaddr 40:8d:5c:c3:9c:be  
          inet addr:169.254.10.181  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:19388 (19.3 KB)  TX bytes:19388 (19.3 KB)






  *-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 40:8d:5c:c3:9c:be
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:27 memory:fdcc0000-fdcfffff ioport:df00(size=128)



```

I checked the drivers too, and there isn't any problem with them.

Actually, now in the Network Manager it says that device is not managed, and the last time the wired connection was active was 4 hours ago.

---

### Post by TheFu on 2017-05-04
And you restarted the networking subsystem after modifying the interfaces file as requested?

---

### Post by mclaren2 on 2017-05-04
i did, and now it connects to the enp2s0 network. still, there is 100% packet loss when pinging.

---

### Post by TheFu on 2017-05-04
> **mclaren2 said:**
> i did, and now it connects to the enp2s0 network. still, there is 100% packet loss when pinging.

**Show your work**, so your statements aren't misunderstood AND are accurate.  I don't know what you mean by the 2nd phrase above. It isn't clear. Please.  Make it easier to help you.

---

### Post by mclaren2 on 2017-05-04
```
[COLOR=#000000]ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.10.181 icmp_seq=1 Destination Host Unreachable
From 169.254.10.181 icmp_seq=2 Destination Host Unreachable
From 169.254.10.181 icmp_seq=3 Destination Host Unreachable
.
.
From 169.254.10.181 icmp_seq=26 Destination Host Unreachable
From 169.254.10.181 icmp_seq=27 Destination Host Unreachable


^C
--- 192.168.1.1 ping statistics ---
27 packets transmitted, 0 received, +27 errors, 100% packet loss, time 35328ms
pipe 4

[/COLOR]

```

[COLOR=#000000][/COLOR]This was done connected to enp2s0.

---

### Post by mclaren2 on 2017-05-05
Ok, I think I've got to the root of the problem. For my internet to work, I have to set up PPPoE. (because of my ISP). But when I do:

```
sudo pppoeconf

Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

```

So when I connect the ethernet cable (to any device) it just tries to connect and then it says "Disconnected Ethernet network". 
Doing:
```
sudo dhclient enp2s0
```
also gives no output, and it doesn't seem to fix it.

---

### Post by TheFu on 2017-05-05
ppp is normally handled by the router as a login to DSL networks.  If you didn't have a router, then yes, you'd need something like that on 1 system and it would effectively have to be the router for your network.

Still waiting to see the new interfaces file.
A fresh **sudo lshw -C network** would be helpful too.  The last one showed a very low connection speed, which usually means there is a cable problem.

---

### Post by mclaren2 on 2017-05-05
It started working, it was ultimately a router problem, I think.
Thanks a lot man, for bearing with me (and my ignorance).

---

### Post by TheFu on 2017-05-05
Nobody is born knowing this stuff. 
We all gain knowledge through experiences.

---

