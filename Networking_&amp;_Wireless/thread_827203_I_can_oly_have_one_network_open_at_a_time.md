---
title: "I can oly have one network open at a time?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Luke has no name on 2008-06-12
When I plugged a LAN cable into my computer, I was disconnected from my wireless. Is there a way around this, or is this a bug?

---

### Post by dmizer on 2008-06-13
nope, no bug. this is expected and desirable behavior which will happen in windows as well.  you cannot have two active ethernet connections on the same subnet.

if (for whatever reason) you want to plug your ethernet cable in, but not use it, you can edit /etc/network/interfaces and remove the "auto eth0" (or whatever  designation your wired adapter happens to be) line.  but this means that you will have to manually mount your wired network adapter every time you connect it.

---

