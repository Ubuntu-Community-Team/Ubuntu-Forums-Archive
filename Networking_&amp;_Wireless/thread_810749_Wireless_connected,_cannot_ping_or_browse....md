---
title: "Wireless connected, cannot ping or browse..."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by MikeRaines on 2008-05-28
Hi guys,

After a couple nights of playing with it I finally got my Broadcom wireless card working.

For a while I could see wireless networks but not connect, I finally fixed this after hours of being lost.

I can now connect to my wireless.

Once connected I can download packages and install updates and software.

i.e
```

sudo apt-get install amarok

```

Worked fine.

I cannot however browse the internet via firefox or ping web sites. I have tried disabling IPv6 and what not but no luck. Hopefully in these forums ill have more luck. Any ideas?

Thanks in advance.

---

### Post by bluefrog on 2008-05-28
fair chance you have nothing in /etc/resolv.conf

you need a nameserver (preferably those of your internet provider

example
gksudo gedit /etc/resolv.conf
nameserver 4.2.2.2

---

### Post by MikeRaines on 2008-05-28
resolv.conf file is populated like this

```

search home
nameserver 10.12.42.5
nameserver 10.12.42.6

```

Any other ideas?

---

### Post by MikeRaines on 2008-05-28
I solved it, thought I would post what I did here for others having the same issue.

Process:
Redisabled IPv6 in /etc/modprobe.d/aliases
Opened Network Manager
Disabled Roaming Mode
Configured for DHCP Auto


I am not sure why this fixed it, since I was launching a dhcp client from the command line to begin with, but im assuming network manager was messing with some of the configurations somehow.

Anyways it's fixed. Hope this helps someone else!

---

