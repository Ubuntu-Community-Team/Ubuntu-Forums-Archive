---
title: "Laptop as router?"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Ripfox on 2007-07-24
I have a laptop that is connected via my wireless router  in my house. In the bassment, I have a desktop with an ethernet card in it only. Is there a way I can run a cable from my laptop to my desktop to connect the desktop to the internet? I have no exp in this, and it just occured to me a few minutes ago that it may be possible...

Any ideas?

---

### Post by dannyboy79 on 2007-07-24
you basically want to use your laptop as a wireless bridge. Yes, this can be done. The cable has to be a cross-over cable NOT a straight thru like you see very often in the stores. Here's some tips on that:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=ics+ubuntu](http://ubuntuforums.org/showthread.php?t=91370&highlight=ics+ubuntu)

---

### Post by Ripfox on 2007-07-24
so not cat5?

---

### Post by dannyboy79 on 2007-07-25
well it's still considered cat5 cable BUT it's called a crossover cable. It still uses your ethernet port.

---

### Post by dmizer on 2007-07-25
if you don't have a crossover cable, some (SOME) recent network adapters are capable of automatically crossing the connection as needed so you may be successful by simply trying a regular lan cable.  also, most hubs and routers are capable of automatically crossing the connection.  if you have a router, be sure to disable network address translation (NAT) so it does not become a dhcp server.  otherwise, you will need a crossover cable.

about a week ago, i attempted to do this very same thing and was not successful with the tutorial dannyboy79 posted.

i WAS successful by following this howto: [https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28translation%29%7C%28address%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28translation%29%7C%28address%29)

notes:
the ip address range you decide to use should NOT be in the same subnet as your wireless connection.  for example, if your wireless ip is 192.168.0.XXX, you cannot use 192.168.0.0/24 for internet connection sharing.  you'll have to use something like 192.168.1.0/24 or 192.168.2.0/24

it's also critical to get your network adaptors in the correct order.
from that howto, replace "eth0" with your wireless adaptor, and replace "eth1" with the adaptor you have directly connected to your desktop.

here is a sample from my own configuration (/etc/network/interfaces):
```
auto eth1
#this is the adaptor with internet access its ip is 192.168.[COLOR="Green"]0.2[/COLOR]
iface eth1 inet dhcp

auto eth2
#this is the adaptor allows a second computer to gain access to the internet
iface eth2 inet static
        address 192.168.[COLOR="Red"]2.1[/COLOR]
        netmask 255.255.255.0
```

now, on my second computer (the one connected via crossover cable), i have it set up with a static ip as follows:
```
iface eth2 inet static
        address 192.168.[COLOR="Red"]2.2[/COLOR]
        netmask 255.255.255.0
        gateway 192.168.2.1
```

post if you have problems or questions.

---

### Post by Ripfox on 2007-07-25
Well, this was all very confusing for me, I must admit. I tried the earlier link and got the desktop to SAY it was connected but no internet. Well, I gave up and now every time I hook up to the wireless network from my laptop, I noticed that the box "static DNS" is checked by default and I have to uncheck it. This even happens after a fresh install...did I change some setting on the wireless router in my process? I am also not sure I made myself clear as to what i want to do. I want to run a cable from my laptop ethernet port to my desktop ethernet port, as my laptop will get wireless but the desktop in the bassment will only hook to the internet through hardwiring. Can I use my laptop which is connected via wireless router as a router to hardwire the desktop to the internet.

---

### Post by dannyboy79 on 2007-07-25
yes, your last statement is what you CAN do. dmizer hit it on the head as he has susccessfully done it. He was merely pointing out that some newer ethernet cards can auto cross the transmission and receiving connection which is what you HAVE to have when connecting to ethernet cards together (meaning not a router or a switch or similar) So I would first TRY the normal cat5 straight thru cable and follow whaty dmizer says and if you don't get it working, then go with the cross over cable from your laptops ethernet port to your desktops ethernet port. hope you got it now.

---

### Post by Ripfox on 2007-07-25
Thanks I will try it.

---

