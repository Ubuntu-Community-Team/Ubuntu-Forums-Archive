---
title: "Ethernet cord not detected..."
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by XDevHald on 2007-07-22
It's been a long time since I have done this, and I don't remember how I got it to work a few years ago, but my ethernet cord is not being recognized. Pretty much about it, any ideas or tips would be great :)

---

### Post by TheDeivix on 2007-07-22
is your ethernet card up? 

type on a terminal:

> ifconfig

this will show you a list with all the network interfaces running, if you don't find your card in this list (eth0 probably), try:

> ifconfig eth0 up

also check if this interface is configured to use DHCP or a manually asigned IP

---

### Post by XDevHald on 2007-07-22
Thanks Deivix, I will give it a shot right now. I also did a static IP but no luck on that either...I DON'T want to go back to Enlightenment but if this doesn't work at all I might have to :(

---

### Post by Rui Pais on 2007-07-22
what's th output of:
```
lspci | grep net
```
and
```
lshw -C net
```
please?


edit:
what do you mean by "go back to Enlightenment"?

---

