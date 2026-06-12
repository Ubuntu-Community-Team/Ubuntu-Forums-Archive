---
title: "[SOLVED] Can receive info from internet, but not transmit"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by malachi1990 on 2008-06-23
So I had internet at school, no problems (with the wired connection).  Come home, and I cant access anything past my laptop.

I used ip route and got this:

169.254.0.0/16 dev eth1  proto kernel  scope link  src 169.254.4.168 
default dev eth1  scope link  metric 1000 


Looks like I'm missing something, just don't know what.

---

### Post by superprash2003 on 2008-06-23
are you trying to access your network wirelessly at home?

---

### Post by malachi1990 on 2008-06-24
No, through a wired connection.

---

### Post by Iowan on 2008-06-24
Static addresses of DHCP? Looks like **avahi** providing address.

---

### Post by malachi1990 on 2008-06-25
Not entirely sure how to do that (I've only recently had time to start seriously learning commands and such, so I haven't gotten that far).

---

### Post by malachi1990 on 2008-07-13
Apparently, this is a problem with the internet connection, and not ubuntu, as my vista partition can't connect either :( .

---

