---
title: "Desperate about wireless internet"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by boriscons on 2006-09-10
Have a wireless PCMCIA card on my laptop. Works fine and I have a local net.
On the other hand I have a 3Com wireless router and my provider with pppoe service but can not get through, i.e. internet?

Please help!

---

### Post by spd106 on 2006-09-12
What is you default route? Try this at a terminal
**ip route**
It should be pointed at the wireless router's ip address.
Also your /etc/resolv.conf should show something like this

[I]search workgroup
nameserver 192.168.1.1[/I]


Assuming the router is at 192.168.1.1.

---

### Post by boriscons on 2006-09-14
I did exactly as you wrote.
Router's ip is 192.168.1.1,
in \etc\resolv.conf there are lines

domain workgroup
nameserver 192.168.1.1

My internal network works fine.
But now I have to establish a connection with my porvider.
This connection should be pppoe. How?
BTW, it works perfectly under Win.

---

