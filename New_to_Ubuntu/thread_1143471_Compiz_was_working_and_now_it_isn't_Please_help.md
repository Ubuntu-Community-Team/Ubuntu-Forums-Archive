---
title: "Compiz was working and now it isn't? Please help?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-04-29
Compiz desktop effects were working, but after I ran a recent update in ibex, desktop are no longer enabled. I tried to turn them back on but I got the message, "Desktop effects can not be enabled". I checked for hardware drivers but found nothing. I also tried "sudo compiz --replace" but nothing changed. 

What can I check next?

The graphix adapter is an onboard intel graphix chipset.

Any help is appreciated.

Powel

---

### Post by theozzlives on 2009-04-29
Seems alot of Intel chips are being blacklisted. It happened on my laptop and I ran compiz-check, just told it to ignore the blacklist. I got compiz back, but on my desktop I had to buy an NVIDIA card to replace my Intel chip.

---

### Post by powel212 on 2009-04-29
Actually I have 2 identical computers side by side and one of them has desktop effects and the other does not. So I checked the /etc/X11/xorg.conf on both to look for differences and they are exactly the same but no desktop effects on one box. Weird.

Help please. I don't know where to look next.

Powel

---

### Post by powel212 on 2009-04-29
Okay things just got even weirder. I created a new user and logged in as the new user and the new user has desktop effects but the orriginal account still does not. Both are admin accounts.

P

---

