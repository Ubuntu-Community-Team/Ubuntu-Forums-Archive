---
title: "Can I make samba accounts for other PCs on my LAN?"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-12-18
Long story short...

I got brother 1, brother 2, and mom. I have some extra space on this pc with my spare hard drive so I figured I'd set up samba so they can map the network drives to their designated folder on the spare hard drive so they can back up their pictures and such.

But I came to the road block where it said something about the samba users must be an existent user on my linux desktop.

Isn't there anyway I can have ubuntu have 1 user, me, and 4 samba users? Me, bro, bro, mom?

---

### Post by heatpumpcontrol on 2007-12-18
I believe you have to add each user into the pc so that samba can allow them access. Otherwise, anyone can view your files while networked and that would defeat the purpose of security.

You can also give 'others' read and write privileges but make sure that your router is well secured. If you have wifi, secure it very well too with a strong encryption.

---

