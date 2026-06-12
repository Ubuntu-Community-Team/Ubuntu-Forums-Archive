---
title: "Cable Modem Immposible"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by _SchmRz_ on 2007-10-22
I have tried everything, it just doesn't want to work.

- I'm connecting my cable modem directly to my network card(Realtek RTL8139 Family PCI Fast Ethernet NIC)
- I've configured my network card in Ubuntu.
- I've installed Penguin PPPOE client, and configured it.

When i try to connect it says "TIMED OUT"...

On Windows it's working normaly. Please help, i really want to start using linux more often.

---

### Post by _SchmRz_ on 2007-10-22
Anyone?

I have read all other topics about cable modems, but i could not solve my problem.

---

### Post by _SchmRz_ on 2007-10-22
nobody?

---

### Post by froy02 on 2007-10-22
Need more info.
open a terminal window and type "ifconfig" then post the results here.

---

### Post by Steve1961 on 2007-10-22
Do you need PPPOE with a cable modem?  I have a Virgin Media cable connection and my Gutsy box just connects at boot up.  As requested, please post the output of ifconfig

---

### Post by _SchmRz_ on 2007-10-22
here is the output

```
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C6:E8:D6  
          inet addr:10.0.25.193  Bcast:10.0.3.255  Mask:255.255.224.0
          inet6 addr: fe80::250:baff:fec6:e8d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5238664 (4.9 MiB)  TX bytes:1182 (1.1 KiB)
          Interrupt:18 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66196 (64.6 KiB)  TX bytes:66196 (64.6 KiB)
```

---

### Post by _SchmRz_ on 2007-10-22
And yes, one more thing... Sometimes when i try to connect (in windows) i get "Line is busy Error 676" Error.

Sometimes i need to try to connect up to 20 times until it succesfully connects on the network.


Sorry on my bad english... I'm from Bosnia.

---

### Post by Steve1961 on 2007-10-22
10.0.25.19 is a non-routable ip address which you generally get if you're behind a router.  I'm presuming, therefore, that your modem is a modem router, and that rather than being directly connected to the internet you're connected to a router which appears to have released an ip address to your Linux box.  Try the following in a terminal:

sudo dhclient eth0

---

### Post by _SchmRz_ on 2007-10-22
I have allready tried that... But i will try it again :)

---

### Post by Steve1961 on 2007-10-22
It could be a dns problem.  Could you post the output of:

cat /etc/resolv.conf

Also:

route -n

---

### Post by _SchmRz_ on 2007-10-22
output of dhclient:

```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on 	LPF/eth0/00:50:ba:c6:e8:d6
Sending on	LPF/eth0/00:50:ba:c6:e8:d6
Sending on	Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.0.3.253
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.03.253
bound to 10.0.25.193 -- renewal in 7103
```

---

### Post by Steve1961 on 2007-10-22
You could also try pinging an ip address.  If you get a reply it's almost certainly a dns problem:

ping -c 3  208.67.222.222

If that works try this:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

and you might find this thread useful:

[http://ubuntuforums.org/showthread.php?p=3222872#p%20ost3222872](http://ubuntuforums.org/showthread.php?p=3222872#p%20ost3222872)

---

### Post by Steve1961 on 2007-10-22
> **_SchmRz_ said:**
> output of dhclient:

```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on 	LPF/eth0/00:50:ba:c6:e8:d6
Sending on	LPF/eth0/00:50:ba:c6:e8:d6
Sending on	Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.0.3.253
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.03.253
bound to 10.0.25.193 -- renewal in 7103
```

Based on this you're connected, so try my suggestions in the previous post

---

### Post by _SchmRz_ on 2007-10-22
resolv.conf:

```
search hs.europronet.ba
```


route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.224.0   U     0      0        0 eth0
0.0.0.0         10.0.3.253      0.0.0.0         UG    0      0        0 eth0

```

---

### Post by _SchmRz_ on 2007-10-22
I will wait until you reply to my last post and then i will try to ping those ip addresses...

Thanks for helping me...

---

### Post by Steve1961 on 2007-10-22
OK try this:

> sudo gedit /etc/resolv.conf

comment out the existing entry and add an additional one so that it looks like this:

> #search hs.europronet.ba
nameserver 10.0.3.253

Then do this:

> sudo/etc/init.d/networking restart


Does it work now?  If not check that network manager hasn't changed resolv.conf back to what it was.  If it has, try the solution in one of the links I posted.

---

### Post by _SchmRz_ on 2007-10-22
I'm back...

First i tried [ping -c 3 208.67.222.222]; says: Network unreachable
Then i changed resolv.conf
Then: [sudo /etc/init.d/networking restart]
Then i checked if resolv.conf has been changed. Everything was fine.
Then i tried [ping -c 3 208.67.222.222]; says: Network unreachable

---

### Post by Steve1961 on 2007-10-22
Not sure what to suggest from here.  Might be an idea to post the output of lspci -v for your network card in case anyone else has any suggestions.

---

### Post by _SchmRz_ on 2007-10-22
Ok, i'l do it...

---

### Post by _SchmRz_ on 2007-10-22
Here it is:

```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
	Subsystem: Asustek Computer, Inc.: Unknown device 8081
	Flags: bus master, medium devsel, latency 32
	Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: [c0] AGP version 2.0

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e7000000-e7ffffff
	Prefetchable memory behind bridge: ef700000-febfffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] (rev 10)
	Flags: bus master, medium devsel, latency 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
	Flags: medium devsel
	I/O ports at e600 [size=32]

0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
	Subsystem: Asustek Computer, Inc.: Unknown device 807a
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at e6800000 (32-bit, non-prefetchable) [size=4K]

0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
	Subsystem: Asustek Computer, Inc.: Unknown device 807a
	Flags: bus master, medium devsel, latency 32, IRQ 23
	Memory at e6000000 (32-bit, non-prefetchable) [size=4K]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
	Subsystem: Asustek Computer, Inc.: Unknown device 807a
	Flags: bus master, fast devsel, latency 128
	I/O ports at d800 [size=16]

0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: Asustek Computer, Inc. CMI8738 6ch-MX
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 17
	I/O ports at a800 [size=256]
	Capabilities: [c0] Power Management version 2

0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: D-Link System Inc DRN-32TX
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at a400 [size=256]
	Memory at e5000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

0000:00:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
	Subsystem: Conexant Dynalink 56PMi
	Flags: bus master, medium devsel, latency 32, IRQ 6
	Memory at e4800000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at a000 [size=8]
	Capabilities: [40] Power Management version 2

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3) (prog-if 00 [VGA])
	Subsystem: Asustek Computer, Inc.: Unknown device 808b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at ef800000 (32-bit, prefetchable) [size=512K]
	Expansion ROM at ef7e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0


```

---

### Post by _SchmRz_ on 2007-10-25
Anyone?

---

### Post by _SchmRz_ on 2007-11-05
OK...

Here's more info:

I can connect when using Windows.
When i run pppoeconf i get: Access Concentrator not found

---

