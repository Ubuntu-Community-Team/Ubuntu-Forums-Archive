---
title: "No internet this time round"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by vbmds on 2007-06-07
I've just re-installed ubuntu 7.04-64 after having a look at some other distros.

However this time round I can not get access to the internet. What I can get is pings to both my DCHP server and my ADSL modem. What is most frustrating about the whole thing is that the server (SME) that hooks into the network via the same switch, has been able to connect and pickup server updates.

Based on advice given in other threads, I've had a look at resolves.conf - which is pointing to my DCHP server, and the interfaces file which seems to be in order.

My laptop has 3 network interfaces, modem - unconfigered, wireless - set to roaming, otherwise unconfigered, Ethernet - set to DCHP and hooked up to network switch.

There is one thing strange about my current internet situation and I am wondering if it tripping ubuntu up - although I'm on broadband, I've used up my data allowance for this month and so am being throttled back to 56K modem speeds - damn its slow. Could this be the reason I can not get onto the internet with ubuntu?

---

### Post by kroiz on 2007-06-07
do you get an IP?
did you use pppoeconf?

---

### Post by vbmds on 2007-06-07
Yes I get an IP and its within the range I've assigned the DCHP server.

No I've not used pppoeconf, it [network] is all how ubuntu sets it up by default.

I would add that this is the 3rd time I've installed ubuntu on this laptop, but this is the 1st time I've had issues with internet access. Further to this, I've also installed kubuntu multiple times without internet issues.

---

### Post by steeleyuk on 2007-06-07
The speed shouldn't be the issue. Sounds more like the DNS servers haven't been defined. Try pinging and accessing this IP address (64.233.183.103) in your web browser. If it works then you'll need to find out your DNS server IP's (or use OpenDNS).

PS. the IP address above is Google

---

### Post by vbmds on 2007-06-07
Sounds reasonable that the DNS servers have not been identified. Knowing the DNS IPs, where does one enter the data in ubuntu?

---

### Post by accord on 2007-06-07
into /etc/resolv.conf, like this:
```
nameserver 140.112.2.198
```

---

### Post by steeleyuk on 2007-06-07
System > Administration > Network > DNS tab

---

### Post by vbmds on 2007-06-07
Ok, well after alot of fiddling I am replying here from ubuntu :D

Just editing the resolv.conf file did not work as everytime I restarted networking my changes were removed and the references to the DCHP server were reinstated. I've had to change to a Static IP and remove all references to the DCHP server and replace them with my ISPs DNS servers. Not ideal but at least I can get back to spaming the clan forum :popcorn:

---

