---
title: "Internet gateway + traffic logging"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by dd86 on 2009-02-03
Hi, I'm going to set up a linux internet gateway but I'm new to linux so I don't know where to start

I want to setup a server so multiple users can connect to the Internet through that so i need to setup some DHCP and NAT but I allso want to log all the internet traffic all the web sites and downloads that the users are visiting on the internet and save it to a file.

I was hoping You could help me with that.

Thanks:)

---

### Post by petervk on 2009-02-04
Read up on Squid and transparent proxying. You can't just check a box to get this running, but it is possible.

You'll probably need two network cards in the server.

Anyone successfully done this? I've attempted and got close.

---

