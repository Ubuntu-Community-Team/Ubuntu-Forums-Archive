---
title: "External Network Drive"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by akschnare on 2007-12-02
I have an external drive that has a network port in the back of it that says that I can connect it to a router and access from any comptuer on the network. I'm wondering how to do this in Ubuntu. 
I have connected it to the router, but I can't seem to find it on the computer. If anyone can help it would be great, thanks.

---

### Post by jonallport on 2007-12-03
Some (more price-concious) network attached drives use a propritary network transport (like iSCSI on the cheap).  It's not IP, it's not routable etc.  The most popular transport seems to be NDAS (network direct attached storage) and there seem to be linux support available for this.

---

### Post by adonet on 2007-12-04
I'm considering to buy one of these so called network drives. It has USB and a network connection. Does Ubuntu 7.10 accept such drive? How does that work? 

Does anyone know if there is an automatic backup program that mirrors every file the system writes on the normal disk to an externel (network or USB) drive?  The drive is shipped with such software for windows, but not for Linux.

---

### Post by jonallport on 2007-12-05
In reply to adonet:

I'd do my homework and look for drives/enclosures that support a more popular protocol.  I know there are drives on the market which support smb and ftp.  I've not bothered messing about with linux support for NDAS, I just use the USB connector!

As for mirroring, have a look at rsync.

---

