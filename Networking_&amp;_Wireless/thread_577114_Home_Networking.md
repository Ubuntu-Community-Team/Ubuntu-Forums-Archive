---
title: "Home Networking"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by thebear1954 on 2007-10-15
I am running Ubuntu with a wireless router. I would like to add another desktop that is running Microsoft XP. How do I set up the microsoft box? Thanks

---

### Post by dmizer on 2007-10-15
what exactly do you mean by "set up the microsoft box"?  what do you want the microsoft box to do?

---

### Post by brn on 2007-10-15
**Similar question.** -- I have installed Fiesty on a four year-old, slightly used but entirely adequate desktop machine to replace a 12 year-old Windows98 box.  I would like to configure this as a "print server" so I can reach the printer from my laptop, also running Fiesty.  Both connect to a DSL modem/router. 

 Ifconfig reports this for the desktop machine:
> eth0      Link encap:Ethernet  HWaddr 00:09:6B:88:FA:53  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe88:fa53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
And for the laptop:
> wlan0     Link encap:Ethernet  HWaddr 00:1A:73:0F:12:DA  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe0f:12da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
How do I configure these so that the two computers can communicate with each other and the laptop can access the printer attached to the desktop?

I'm sure that this is fairly straightforward but must confess that I am a network newbie.

-Thanks-

---

### Post by dmizer on 2007-10-16
> **brn said:**
> How do I configure these so that the two computers can communicate with each other and the laptop can access the printer attached to the desktop?

I'm sure that this is fairly straightforward but must confess that I am a network newbie.

-Thanks-

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

works with windows or ubuntu clients.

---

### Post by brn on 2007-10-16
> **dmizer said:**
> [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

works with windows or ubuntu clients.

Works very nicely for Ubunto.  -- Thanks again.

---

