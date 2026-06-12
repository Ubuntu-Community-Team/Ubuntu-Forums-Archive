---
title: "Help with Networking"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by prospect on 2007-03-08
Hey guys,

I just installed Ubuntu 6.10 the edgy eft on my sony vaio laptop and everything is smooth so far sound working screen display perfect but can't get online I am using a webstar router already connected to the net i used it on windows but when i plugg it in the laptop and fire up firefox nothing happens.

I did read a little about netowkring and I've tried this

System > Networking > and i saw the three options and Wired connection is activated DHCP but still nothing ,...

Please help

---

### Post by chili555 on 2007-03-08
Please tell us the outcome when you open a terminal and type ifconfig. Also, does Firefox just grind away and return nothing, or does it immediately report "Server not found"? If it's the former, you might try disabling ipv6 in Firefox by typing about:config in the address bar, filtering for ipv6 and double-clicking the entry **network.dns.disableIPv6** so you change false to true. Close Firefox and open and try again.

---

### Post by prospect on 2007-03-08
okai I don't know if this will help but when i enable the wireless button i connect to a random connection thinks it my neighbours and firefox works fine the ipv6 is disabled

but when i plug in my ethernet nothing happens , this what i get when i type in ifconfig

eth0
Link encap:Ethernet
RX packets:23904 errors:0
TX packets:26
rx bytes: 1545655 tx byte:7308

eth1
Link encap:Ethernet
RX packets:0
TX packets:0
rx bytes: 329635  tx byte:98647

lo
Link encap:Ethernet
RX packets:754
TX packets:754
rx bytes: 67888 tx byte:67888

oh yeah firefox says Server Not found

I've tried

$ sudo ifdown eth0
$ sudo ifup eth0

and my eth0 connection wasn't enabled in my network connections

---

### Post by prospect on 2007-03-08
okai guys please someone help around here!!!!

regards

---

### Post by chili555 on 2007-03-08
Is it possible that *both* wired and wireless are trying, unsuccessfully, to connect? That's part of what I was driving at by asking for ifconfig. It would have been helpful to see more information. You posted, for eth1: ```
eth1
Link encap:Ethernet
RX packets:0
TX packets:0
rx bytes: 329635 tx byte:98647
``` and ifconfig usually looks like this; ```
Link encap:Ethernet  HWaddr 00:02:6F:09:5A:6F  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe09:5a6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34338151 (32.7 MiB)  TX bytes:2340862 (2.2 MiB)
          Interrupt:3 Base address:0x2100 

```

Please try sudo ifdown eth1 followed by sudo dhclient eth0. Please let us know the result. More information, like beer and chocolate, is better than less.

---

### Post by prospect on 2007-03-08
nah its okai I am installing windows back, if a simple thing like getting online with wired connection is that much hasstle i don't think this syetm is worth it... plus the fact you guys not that helpfull no disrespect chili555 took you time but atleast you actully tried to help me..

thanks
regards

---

### Post by chili555 on 2007-03-08
Well, you gave it a helluva try...

---

### Post by prospect on 2007-03-08
well I can't type up all the result and you haven't asked for anything specfic mateplus take you guys hours even acknowledge posters i saw other people still without anyone to answer their posts , however you did help and i acknowledged that so no need to be sarcastic 
again regards

---

