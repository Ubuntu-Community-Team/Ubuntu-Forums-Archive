---
title: "My XP-&gt;Ubuntu VNC is slooooooooow"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by sipickles on 2007-11-11
Hi,

I use both XP and Ubuntu. I've been trying to use VNC to control my penguin from XP, and it works but is very slow. Like 1 fps when more than a small part of the screen changes.

I've tried vncserver and x11vnc on the Ubuntu box, and ultraVNC and tightVNC clients on XP.

All with pretty much the same results.

Can it go any quicker with some magic? its really not usable. With both machines running XP and UltraVNC it was many times qucker.

Thanks for your advice

S

---

### Post by cybertoast on 2007-11-11
I would strongly recommend FreeNX, which is much faster and more flexible (in my experience) than VNC. THey're at [http://nomachine.org](http://nomachine.org).

---

### Post by sipickles on 2007-11-12
Yeah, I've installed the free linux version of Nomachine NX.

Amazing.... it literally wees all over VNC :guitar:

---

### Post by serpentine on 2007-11-14
> **cybertoast said:**
> I would strongly recommend FreeNX, which is much faster and more flexible (in my experience) than VNC. THey're at [http://nomachine.org](http://nomachine.org).

cybertoast,

NoMachine is no longer affilated with the FreeNX project for quite some time now.  Your link points to the NX Free Edition product that is produced by NoMachine themselves.  You can see some background here:

[http://www.nomachine.com/news-read.php?idnews=202]("http://www.nomachine.com/news-read.php?idnews=202")

[http://www.nomachine.com/ar/view.php?ar_id=AR10C00298]("http://www.nomachine.com/ar/view.php?ar_id=AR10C00298")

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by Skip Da Shu on 2007-11-18
> **daflame said:**
> If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

Is it possible to set it to only allow 1 connection at a time?

---

