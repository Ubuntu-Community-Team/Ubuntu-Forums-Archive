---
title: "Power Manager: Sleep Problem."
date: 2010-01-01
forum: New to Ubuntu
---

### Post by soryu on 2010-01-01
I Recently Got Hibernation To Start Working On My PC.
(i sudo configured my nvidia driver display settings)
it was waking up to a black screen.
 now it wakes up to whatever was on the desktop.
but i get a message that says,
 Power Manager:Sleep Problem look in help.

anyone with a similar problem?

---

### Post by inobe on 2010-01-01
did you install ubuntu with wubi ?

---

### Post by Paqman on 2010-01-01
> **inobe said:**
> did you install ubuntu with wubi ?

Wubi-installed systems cannot hibernate.

Soryu: what exact model of computer do you have? Sleep and hibernate bugs are not uncommon, and are usually down to the specific type of hardware.

---

### Post by soryu on 2010-01-01
Compaq Presario5000 series (kinda old)


jaunty CD, upgrade to karmic.

---

### Post by Paqman on 2010-01-01
Sounds like you might have some wee bug in the system, but at least it's not causing too many problems.

You could have a bit of a trawl through the logs at /var/log/kern.log. If you want help with the contents, feel free to post them here and someone will take a look over them.

---

### Post by soryu on 2010-01-01
cannot open log 
 gedit can't detect coding please check that you are not trying to open binary file.

both logs 
kern.log
kern1.log

---

