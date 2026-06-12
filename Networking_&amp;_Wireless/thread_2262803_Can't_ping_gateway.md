---
title: "Can't ping gateway"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by Tom_Wilson on 2015-01-27
Hi all, I installed a fresh Ubuntu Server 14.04.1.  I've configured it properly as far as I can see but no matter what I do I can't ping... anything.  It did work for a few minutes, then I added the dns-serveraddress to the interfaces file and since then it's been a train wreck.  So much so I've reinstalled the server 3 times and get the same result.  The cable I'm using is fine. plugged into a windows machine it works perfectly.  My interfaces file:

address 10.0.4.28
netmask 255.255.255.0
network 10.0.4.0
broadcast 10.0.4.255
gateway 10.0.4.1
dns-nameserver 10.0.4.25
dns-search mydomain.com

netstat -rn:

Destination  Gateway  Genmask  Flags  
0.0.0.0  10.0.4.1  0.0.0.0  UG  eth0
10.0.4.0  0.0.0.0  255.255.255.0  U  eth0

Any ideas?  Thanks!

---

### Post by ian77 on 2015-01-27
You should have something like:

```

auto eth0
iface eth0 inet static

```

before all your network config in your interfaces file.

What does the console say when you try and ping the gateway?


Confirm you can ping your loopback at 127.0.0.1
Need to confirm this before you try anything else really.

**Arp**
First thing to check is your ARP table. After trying to ping your default gateway the ARP table should contain your default gateway's MAC address. 
Ping won't work unless this is populated.

Can you ping other devices on your LAN? Do their MAC addresses enter the ARP table?

**IP**

If the ARP table is working properly, the issue is likely with the IP addressing. Either a conflict or incorrect addressing is the most probable cause.

Cheers

---

