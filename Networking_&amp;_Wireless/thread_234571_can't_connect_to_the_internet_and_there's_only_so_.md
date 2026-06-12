---
title: "can't connect to the internet and there's only so much gnometris i can play"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by fredbaluga on 2006-08-11
My shiny new d-link 300t came in the post today. Alas, the internet doesn't seem to want to work.

I've searched this and other forums and attempted to remedy the situation, but not much seems applicable to my predicament or distribution.

It's all plugged in correctly (it goes into the phone shaped hole in the wall and the ethernet shaped hole in the back of my computer with minimal effort).

Some things that were asked for in other posts that may be of help here:

```
pppoeconf output:
	Sorry, I scanned 1 interface, but the Access
	Concentrator of your provider did not respond. Please
	check your network and modem cables. Another reason
	for the scan failure may also be another running pppoe
	process which controls the modem.

cat /etc/network/interfaces output:
	auto lo
	iface lo inet loopback

	auto eth0
	iface eth0 inet dhcp

	auto eth1
	iface eth1 inet dhcp

	auto eth2
	iface eth2 inet dhcp

	auto ath0
	iface ath0 inet dhcp

	auto wlan0
	iface wlan0 inet dhcp


	iface dsl-provider inet ppp
	provider dsl-provider

	# added by pppoeconf
	auto modconf
	    iface modconf inet manual

	    pre-up /sbin/ifconfig modconf up # line maintained by pppoeconf

cat /etc/resolv.conf output:
	nameserver 192.168.1.1

route -n output:
	Kernel IP routing table
	Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
	192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
	0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

ifconfig output:
	eth0    Link encap:Ethernet  HWaddr 00:13:8F:48:7F:AF
		inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
		inet6 addr: fe80::213:8fff:fe48:7faf/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:465 errors:154 dropped:0 overruns:0 frame:154
		TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000
		RX bytes:140074 (136.7 KiB)  TX bytes:95015 (92.7 KiB)
		Interrupt:58 Base address:0xdead

	lo	Link encap:Local Loopback
		inet addr:127.0.0.1  Mask:255.0.0.0
		inet6 addr: ::1/128 Scope:Host
		UP LOOPBACK RUNNING  MTU:16436  Metric:1
		RX packets:15 errors:0 dropped:0 overruns:0 frame:0
		TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:0
		RX bytes:1996 (1.9 KiB)  TX bytes:1996 (1.9 KiB)

router ping output:
	--- 192.168.1.1 ping statistics ---
	8 packets transmitted, 8 received, 0% packet loss, time 6999ms
	rtt min/avg/max/mdev = 0.619/0.652/0.751/0.039 ms

google ping output:
	--- 64.233.189.104 ping statistics ---
	8 packets transmitted, 0 received, +8 errors, 100% packet loss, time 6999ms
```

internet is provided by Wanadoo, which i think is now called Orange. it was previously called freeserve, and my parents computer (which i'm using now)
connects to it with a .freereve account. showmyip.com informs me that my ISP is actually Energis UK and that im current assigned a host name at .telh.dsl.pol.co.uk
The wanadoo installation cd (for windows) insists on a call centre friendly usb speedtouch modem which i dont really want to use.

htp://192.168.1.1 sends me to a configuration gui dealie when plugged into a XP machine, but in my Ubuntu box Firefox never manages to connect.

It obviously recognises that I have a modem, but i'm not sure what to do from here.

Any help will be greatly appreciated.

p.s. Does anyone know why Amazon sends very small products in enormous amounts of packaging?

---

