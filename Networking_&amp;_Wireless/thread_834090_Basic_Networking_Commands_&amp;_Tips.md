---
title: "Basic Networking Commands &amp; Tips"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by zombrax on 2008-06-19
Hey guys,

Wanting to learn a bit more on the networking side of things; 

like commands, ip lookup, setup static addresses, setup domain/home network etc etc

where is the best place to look at/read etc?

I know this is a bit vague but any input to where i can readup on it would be very helpful.

many thanks

---

### Post by Iowan on 2008-06-19
[http://help.ubuntu.com]("http://help.ubuntu.com") is a good start.  [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") has some step-by-step articles for setting up various servers, etc.
There's a [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") forum, too.

---

### Post by tcpip4lyfe on 2008-06-19
It's really helps to have a background in network theory. Pick up Cisco CCNA 1-4 and you'll get some really solid theory on how networks work.  It starts really slow but I went from knowing nothing about networking to knowing the inner-workings or SONNET rings. 

The best way to learn quickly though is to go to howtoforge and setup a ton of different networks for fun.  Don't just copy and paste the commands but type them out and if you don't know what a command does, man it.  I bet after a week or so of that you'll be able to do the basics like set static IP's or renew DHCP leases.

---

### Post by zombrax on 2008-06-20
many thanks fellas :)

---

### Post by zombrax on 2008-06-28
could anyone please help out with terminal commands for

viewing your Ip config
releasing this IP
renewing/requesting for a new ip

many thanks.

---

### Post by tcpip4lyfe on 2008-07-08
viewing your Ip config- ifconfig
Releasing and renewing- sudo /etc/init.d/networking restart

---

