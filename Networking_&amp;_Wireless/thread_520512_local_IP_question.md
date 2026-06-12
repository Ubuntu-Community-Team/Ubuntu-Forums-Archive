---
title: "local IP question"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by Elf on horseback on 2007-08-08
GENERAL NETWORKING QUESTIONS ONLY

To start off I'm still really new to Ubuntu.  I have been trying to get my PDA to sync with my PC all I need is the anwser to a few small general Wi-Fi questions that i could not find anwsers to in the forum or Google (probably searching with the wrong phrase). 

What is my local IP address?

 Is there a way to find out my local IP address and "lock it" in so when ever i reboot i have the same IP address?

Those are the only 2 questions I have, any help would be great

---

### Post by rickyjones on 2007-08-08
You can discover your IP address by opening a terminal window and typing the command "ifconfig -a" and then hitting the enter key on your keyboard. This is the console way. You can also check it using the GUI but I'm not confident in recalling the steps from memory right now.

You can set a static IP address to ensure that you always have the same IP. Another option would be modifying your DHCP server (the router I assume) to give you the same IP all the time - a lot of routers let you do this. My experience with routers has been that it usually gives you the same IP unless you have a lot of computers constantly connecting and disconnecting.

Hope it helps!

-Richard

---

### Post by Elf on horseback on 2007-08-08
I ran "ifconfig -a" and I got:

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:A9:30:CE:4B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:16:6F:95:F9:51  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe95:f951/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39465 errors:8 dropped:8 overruns:0 frame:0
          TX packets:22290 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:18206357 (17.3 MiB)  TX bytes:5318119 (5.0 MiB)
          Interrupt:22 Base address:0x4000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1704 (1.6 KiB)  TX bytes:1704 (1.6 KiB)

```

does this mean my local IP address is 192.168.1.101?

also i have 3 computers, does that count as a lot? and how do i set up a static IP address on a linksys router? I already know the routers IP address, username, and password.  Thanks

---

### Post by rickyjones on 2007-08-08
> **Elf on horseback said:**
> I ran "ifconfig -a" and I got:

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:A9:30:CE:4B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:16:6F:95:F9:51  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe95:f951/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39465 errors:8 dropped:8 overruns:0 frame:0
          TX packets:22290 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:18206357 (17.3 MiB)  TX bytes:5318119 (5.0 MiB)
          Interrupt:22 Base address:0x4000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1704 (1.6 KiB)  TX bytes:1704 (1.6 KiB)

```

does this mean my local IP address is 192.168.1.101?

also i have 3 computers, does that count as a lot? and how do i set up a static IP address on a linksys router? I already know the routers IP address, username, and password.  Thanks

Yes, your local IP is 192.168.1.101.

I'm not positive on how to set up the client static IP on a linksys router, I've never actually done it. It might be called Reserved IP or something similar.

-Richard

---

### Post by Elf on horseback on 2007-08-08
thanks for your help Richard.  I'll look over google for how to set the router

---

### Post by Austin_KW on 2007-08-08
You set up static IP address on the client, not the router, i.e., you manage them. 
If you use both static and dhcp addressing, make sure you allocate your static IP addresses from outside the pool of addresses assigned to dhcp.

Otherwise, If you want dhcp to always allocate the same address to a device then your router may have this option. Something similar can be to increase the dhcp lease time on the router.

---

### Post by rickyjones on 2007-08-08
You are very welcome!

-Richard

---

