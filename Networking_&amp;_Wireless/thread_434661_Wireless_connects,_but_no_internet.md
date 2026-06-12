---
title: "Wireless connects, but no internet"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by vdubber on 2007-05-06
Hi, I've installed Dapper and connected a Linksys WUSB54Gv4. I followed the instructions to setup the wireless connection and can see my network. I have tried static and DHCP both work, for the network, but I still cannot connect to the web using Firefox. BTW I can ping addresses no problem.

Can anyone suggest if I've missed something obvious as I'm new to networking and Ubuntu?

---

### Post by Mr_Starscream on 2007-05-06
Perhpas you are using an older version of ndiswrapper?

---

### Post by vdubber on 2007-05-06
I'm using ndiswrapper-1.8, as directed in the sticky guide at the top of the page. I can't understand how I can ping an ip adress, but can't see a web page?

---

### Post by agurk on 2007-05-06
Sounds to me like you either have a DNS or an MTU problem. Could you please post the outputs from the commands "ifconfig" and "route"?

(Also, please check that Firefox is configured  to use direct connection and not a proxy: Firefox -> Edit -> Preferences -> Advanced -> Network -> Settings...)

---

### Post by vdubber on 2007-05-06
Thanks for the help, output from the commands, and Firefox is set to direct connection
```
jez@jez-ubuntu:~$ ifconfig

lo      Link encap:Local Loopback
          
	inet addr:127.0.0.1  Mask:255.0.0.0
          
	inet6 addr: ::1/128 Scope:Host
          
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
	RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          
	TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          
	collisions:0 txqueuelen:0
          
	RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)



wlan0   Link encap:Ethernet  HWaddr 00:12:17:96:84:69
          
	inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          
	inet6 addr: fe80::212:17ff:fe96:8469/64 Scope:Link
          
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
	RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          
	TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          
	collisions:0 txqueuelen:1000
          
	RX bytes:2459 (2.4 KiB)  TX bytes:1818 (1.7 KiB)



jez@jez-ubuntu:~$ route

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0

default         mygateway1.ar7  0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by agurk on 2007-05-06
Hmm, it says your gateway is mygateway1.ar7, that doesn't sound right to me. I'm guessing your gateway should be 192.168.1.1 (same IP as your router).
Also, what DNS address do you use? (the "dig" command should show your DNS address at the end)

---

### Post by vdubber on 2007-05-06
Its fixed!!!
Just remembered I had a similar problem when I first tried Ubuntu through VMware.

The solution is to disable IPv6 in Firefox.........suddenly everythings works!

Thanks for the help, and hope this might help others

---

