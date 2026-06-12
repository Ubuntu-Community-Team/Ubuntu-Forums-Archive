---
title: "Driver compilation problem"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by GeertPoels on 2007-03-14
Hello,

I'm trying to compile a driver for a Belkin Wireless Mimo plus F5D9050.
This driver is supposed to support that device :
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

When doing a make, I get:
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** No rule to make target `Mimo'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'

I've downloaded the sources which were put gzp'd in /usr/src.

Were might this error be coming from ?

Does this linux-headers folder contains all sources ? 
Looks like they don't.

Do I need other software ?
(installed everything and more to do a kernel compilation)

Geert

---

### Post by Kobalt on 2007-03-14
Did you simpley install the 'linux-headers-2.6.17-11-generic' packages through Synaptic ?

---

### Post by GeertPoels on 2007-03-15
I can't remember if I did it or they were there, but I definitely re-installed them when this compilation failed.  Also installed the sources, etc.  through Synaptic

---

### Post by GeertPoels on 2007-03-18
An idea, anybody ?

---

