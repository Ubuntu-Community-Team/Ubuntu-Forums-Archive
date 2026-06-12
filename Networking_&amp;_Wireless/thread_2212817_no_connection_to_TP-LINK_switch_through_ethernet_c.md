---
title: "no connection to TP-LINK switch through ethernet cable"
date: 2014-03-23
forum: Networking &amp; Wireless
---

### Post by timbo3 on 2014-03-23
I just bought a new switch so I could connect my laptops to the internet through it since I don't want to use wireless. If I understand it correct, the switch should automatically connect to  all laptops and the internet and learn all mac-addresses. The problem I have is that one of my laptops doesn't even recognise the connection. With the other one, internet works perfectly. And if I connect to the faulting laptop to the internet directly via the cable there is also internet. But somehow, when I connect it through the switch nothing happens.

I'm very new to switches and networking generally so any advice has to be pretty direct. I also prefer using the terminal.

Some info:
The switch is an TP-LINK TL-SG105 and I connect it to the internet via an ethernet cable to the socket in the wall.
I run Ubuntu 12.10 on both my laptops.
The laptop that doesn't see the connection is an ASUS X52J and is a at least four years old.
The other laptop that does get a connection is new from last year if that has anything to say.

---

### Post by Easy Limits on 2014-03-23
Try using different cables to different ports on the switch to connect to your laptop that is not connecting.

---

### Post by timbo3 on 2014-03-23
I have done that. But all cables and ports work with the one but not the other.. However when I put the cable directly in the laptop and not via the switch, it has connection.

---

### Post by houstonbofh on 2014-03-23
Is it a Green Switch?  Some laptop nics (OK, one, but a lot of people used it) have a bug with green gigabit networks, and link never comes up.  Try plugging into a Fast Ethernet port.  (Or post what your nic is.)

---

