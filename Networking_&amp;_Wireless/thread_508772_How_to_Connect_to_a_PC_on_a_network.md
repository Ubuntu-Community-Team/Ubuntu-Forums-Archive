---
title: "How to Connect to a PC on a network"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by gfg5 on 2007-07-24
hi .. 
i m having a little problem .. i m a new user to ubuntu linux . and i am connected to a wireless LAN . i want to open a pc in nautilus ( ubuntu explorer ) but how to do that . i dont know .. 
 in windows i just simply go to run and write the command " \\ ip address "
and the computer is opened but how to do the same thing in ubuntu ?? i dont know . help me .

---

### Post by wjp.reg on 2007-07-24
> **gfg5 said:**
> hi .. 
i m having a little problem .. i m a new user to ubuntu linux . and i am connected to a wireless LAN . i want to open a pc in nautilus ( ubuntu explorer ) but how to do that . i dont know .. 
 in windows i just simply go to run and write the command " \\ ip address "
and the computer is opened but how to do the same thing in ubuntu ?? i dont know . help me .

It really depends on how far you have come in setting up your network.  Perhaps you could say a little more about your configuration efforts or search the forum for a "howto" on windows networking.

None of this should be very difficult with a little more information :-)

If everything is set up usingh SAMBA you should be able to reach your windows share in Nautilus by entering something like:

> smb://winserver/share

in the address line.

good luck!!

---

