---
title: "WAN miniport PPP0E connection setup on ubuntu"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by yesar92 on 2009-08-11
Hello all,

I have just installed ubuntu from a live CD inside Windows Vista and I want to express my absolute admiration for the system , it is great! 

The main Issue I face is that I cannot connect to my WAN MINIPORT PPPOE connection , usually on Vista I simply connect to the wireless network and create a new PPPOE connection with the user id and password I have under the name broadband connection.

I dont seem to know how to configure the connection in the Network client available on ubuntu as I dont know what to choose either IPV4 LL or DHCP , also I don't know the addresses like mask , IP and gateway.

**When simply clicking on the network icon on the upper bar some networks appear and I choose the one I'm associated with but when I choose to connect using ppp0 modem nothing appears! although I am connected to it but when I see the connection information all values are zeros just showing my MAC id.**

Please help me as I plan to share ubuntu with other friends because I think it must has a chance! 

Thank you in advance! 

Yesar Almaleki - Iraq (Basra)

---

### Post by googeek on 2009-08-12
I used "sudo pppoeconf"

---

### Post by yesar92 on 2009-08-14
I already used sudo pppoeconfig and it found no PPPoE connections on both eth0 and ath0 , btw whats the difference between them? (eth0 & ath0)

---

### Post by superprash2003 on 2009-08-14
eth0 and ath0 are two different interfaces if you have 2 LAN cards or 1 LAN and 1 wifi

---

