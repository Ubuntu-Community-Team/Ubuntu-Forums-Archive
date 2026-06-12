---
title: "Building a Linux dual WAN router"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by muqtadr on 2008-08-12
I currently have two network cards in my XP box with a different modem connected to each. My goal is to route traffic from application A over modem 1, and application B over modem 2. Note that I am not trying to combine the two modems and do load balancing. I need to keep them separate for different applications, for example one modem will handle web surfing and the other will handle file sharing.

As far as I can tell my goal is not attainable natively in Windows XP so I was considering building a Linux box with three network cards and setting it up so that two of the NICs would act as WAN ports connecting to my modems and the third will be the LAN port that goes to my Linksys router which would feed my XP machine and wireless network. Question is, is it possible to configure the Linux box to route traffic through a specific WAN port depending on which application on the XP machine the traffic is coming from, and if so, how?

---

### Post by palitone on 2008-12-06
In principle i think you can attain this using 2 routers connected to one switch or hub. Just disable DHCP in those routers and separate lan IPs. Then assign individual workstations static IP addresses, use routers internal IP in the gateway. If you want to join both connections in one server you gonna play around with iptables, http request goes to this ethernet and p2p request goes to the other NIC.

---

### Post by jbarbieri on 2010-01-18
[http://ubuntuforums.org/showthread.php?p=8129464](http://ubuntuforums.org/showthread.php?p=8129464)

---

