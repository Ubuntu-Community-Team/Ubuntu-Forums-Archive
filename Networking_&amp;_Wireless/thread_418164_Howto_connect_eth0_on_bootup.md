---
title: "Howto connect eth0 on bootup?"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by dalee on 2007-04-22
Hi,

I'm having trouble getting eth0 to automatically connect to the internet, (DSL).

It works fine if I manually start it. But I need it to auto connect for my family. It did so in Dapper and Edgy.

Using Feisty Fawn, and my /etc/network/interfaces looks like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

It should connect eth0 automagiclly with this configuration correct?

Thanks!
dalee

---

