---
title: "eth0 idle, but packages recieved/sent. Help (and thanks!)"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by theecube on 2007-10-11
So I recently tried to set up wireless on Ubuntu, but figured that Ethernet would be easier.  Apparently not.  After running pppoeconfig, all the steps seemed to work but Firefox can't load any pages.  I'm connecting through a Linksys WRT54G router, using a Briteport DSL modem. If you have any ideas, here's some information.

ifconfig gives:
```
eth0
	Link encap:Ethernet
	HWaddr 00:11:2F:98:7E:09
	inet addr:192.168.1.101
	Bcast:192.168.1.255
	Mask:255.255.255.0
	inet6 addr: fe80::211:2fff:fe98:7e09/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	RX packets:270 errors:0 dropped:0 overruns:0 frame:0
	TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:19828 (19.3 KiB)  TX bytes:8562 (8.3 KiB)
	Interrupt:209 Base address:0xe000

lo
	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX packets:256 errors:0 dropped:0 overruns:0 frame:0
	TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:20683 (20.1 KiB)  TX bytes:20683 (20.1 KiB)
```

while lspci gives:
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:08.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

and, just for extra info, the Conneciton Properties window says:

(Support Tab)

```
Internet Protpcol (IPv4)
Address: 192.168.1.101
Broadcast: 192.138.1.255
Subnet Mask: 255.255.255.0

Network Device
Type: Ethernet
Address: 00:11:2F:98:7E:09
```

(/Support Tab)


Thanks a million for any information or tips!

---

### Post by jimrz on 2007-10-11
check to make sure that you have proper dns servers listed in System > Administration >  Network

---

### Post by theecube on 2007-10-11
Is there more than one "proper" DNS server?
All I have listed is 192.168.1.1

Thanks

---

### Post by jimrz on 2007-10-12
> **theecube said:**
> Is there more than one "proper" DNS server?
All I have listed is 192.168.1.1

Thanks

that sounds like the IP of your router. check with your isp and see what the IP for a proper dns server is or, if you are dual booting or have a another machine that is able to connect, look there to see what it is using. failing those, ask around locally to see if a freind can give you the info, any dns server will work but it is best if you use one close to you. if all else fails, I'll give you the ones I use

---

### Post by theecube on 2007-10-14
Well, that seemed to work. Thanks!
But....
The connection is ungodly slow.  It seems to be idle most of the time, only sporadically sending/recieving packets.  But at least the connection is going through, mm?

---

