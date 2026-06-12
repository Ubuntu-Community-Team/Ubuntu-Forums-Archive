---
title: "Converting lan to Ubuntu Server"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by PAVED Arts on 2006-11-30
Hello. We currently have an openbsd server and I would like to
switch over to a new machine running ubuntu server 6.10.
Right now I have configured ubuntu with 
eth0 - static ip (adsl modem)
eth1 - gigabit nic plugged into giga switch (mac osx machine mostly)
eth2 - megabit nic plugged into mega switch (everything else - win2k/xp etc)

So far I am able to ping the net and download packages etc.

Right now we use our isp for dns. Openbsd handles some a dhcp server for laptops and stuff.

How do I set up a bridge or whatever it is called to connect eth0 to the other nics?

thanks!

---

