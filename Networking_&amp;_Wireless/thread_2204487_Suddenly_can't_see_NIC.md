---
title: "Suddenly can't see NIC"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by bangla2 on 2014-02-08
Hi,

I've had Ubuntu 10.4 installed for some time, no problems. Suddenly one morning I couldn't get online. After much research (including here) and troubleshooting, I still can't seem to fix it.

Evidently (?) Network Manager overwrote /etc/network/interfaces such that 
iface eth0 inet dhcp

was remmed-out a la:

#iface eth0 inet dhcp

So I unremmed-it and restarted, but the NIC is still not seen

Does anyone know how to get this machine to auto-detect the NIC on restart, 
like a normal decent computer can, and like it once did, before it didn't?

I see that many people have many similar problems along these lines.

Many thanks.

---

### Post by Iowan on 2014-02-08
What else is in */etc/network/interfaces*?
(Personally, I prefer to let NM handle things.)

---

### Post by bangla2 on 2014-02-08
#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by Iowan on 2014-02-08
I was curious if the "auto eth0" line was there.
What are results of 
```
ifconfig -a
```

---

### Post by bangla2 on 2014-02-08
eth0 Link encap:Ethernet HWadr 00:1e:4f:f3:30:11

sorry, I have to type this from that machine to this one, but that line shows it sees the NIC, yes?

---

### Post by Iowan on 2014-02-08
Well, it knows there is one there... This is how mine looks:
```
iowan@work:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:07:a2:01:6f:8b  
          inet addr:192.168.1.13  Bcast:192.168.104.255  Mask:255.255.255.0
          inet6 addr: fe70::208:a2ff:fe01:6f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106638650 (106.6 MB)  TX bytes:9897923 (9.8 MB)
          Interrupt:16 Base address:0xeb00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:237648 (237.6 KB)  TX bytes:237648 (237.6 KB)

iowan@work:~$ 
```
First thought is a failed driver update (although 10.04 went EoL in April 2013)
Next thought is failed ethernet card - hoping to be wrong on both counts.
Check/post results of ```
sudo lshw -C network
```

---

### Post by bangla2 on 2014-02-08
sorry, but can you tell me specifically what to look for, or post, as I have to type it over here. thanks

---

### Post by Iowan on 2014-02-08
I'm reaching my limits, but other guru's will be interested in the product and configuration.

---

### Post by bangla2 on 2014-02-08
thanks for your help

it's an Intel 82566DM-2 Gigabit Network Connection

I'm starting to suspect the NIC may be fried

thanks again

---

### Post by chili555 on 2014-02-08
I believe your device uses the driver *e1000*. When you ran sudo lshw -C network, did it show the driver like this?> *-network       
       description: Ethernet interface
       product: whatever Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       [COLOR="#FF0000"]logical name: eth0[/COLOR]
       version: 06
       serial: f0:de:f1:3e:b2:a4
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="#FF0000"]driver=e1000 [/COLOR]driverversion=2.3.2-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f2600000-f261ffff memory:f2625000-f2625fff Did it show a logical name; that is an interface eth0? Is there any change if you load the driver?```
sudo modprobe e1000
```Any errors or informative messages?```
dmesg | grep -e e1000 -e eth0
```We won't know what's wrong or what to try unless you can help us with some diagnostics.

---

### Post by bangla2 on 2014-02-08
logical name: eth0

driver: e1000e driverversion=1.0.2-k2

"dmesg | grep -e e1000 -e eth0"

yields:

"eth0: link is not ready"

"e1000e: eth0 NIC Link is Down"

---

### Post by Iowan on 2014-02-08
Verify that the network connection is solid.
(Check cable connection - maybe try a different router port...)

---

### Post by bangla2 on 2014-02-08
router works fine with Mac I'm using now

blinking lights on Ubuntu NIC, plugged and unplugged repeatedly, nice clean click

---

