---
title: "virtual pc moved to another host..."
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by jefg60 on 2006-08-08
...and ubuntu 6.06 server still works within it, except that it keeps refusing to configure the network card.

I have it configured with a static IP, but when running:

/etc/init.d/networking restart

or 

ifconfig eth0 up

I get a message saying "eth0 no such device".

lspci lists the DEC virtual network adapter as eth0, and the "tulip" module is loaded.

I thought this was to do with the host it had been copied to / the act of copying the VM to another host, but another VM running arch linux still works (with networking) in the same circumstances. Whats going on?

p.s. I would just use the arch linux VM, but I havent got request tracker 3.4 to work on that one yet. There are no packages for arch and there are packages for ubuntu.

its been moved from a windows XP host to a Windows 2003 server host.

---

