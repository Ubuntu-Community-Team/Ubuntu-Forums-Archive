---
title: "Lost Xubuntu"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by worlestone on 2011-07-04
I have had Xubuntu and Lubuntu running on my laptop for the last few months, mostly as I wanted to try them back to back.  I mostly used Xubuntu.

Unfortunately I ran the upgrade to Lubuntu (to 11?) last week and since then I do not get the option to boot into Xubuntu, it just loads Lubuntu.

I have tried using Super Grub to retriev this option, but to no availe.  Could someone please suggest something else to try and revive Xubuntu?

Thanks

---

### Post by Psyco430404 on 2011-07-04
maybe its a login manager issue, which login manager are you useing??? The default for XFCE or LXDE???

---

### Post by pikpok on 2011-07-04
You're talking about 2 distros installed on other patitions, or 2 graphical environments in one system? If it's the first option, type **sudo update-grub** in OS, which have GRUB installed. It should find all OS'es and add entries each of them to GRUB.

PS. thanks for correcting Bucky :)

---

### Post by Bucky Ball on 2011-07-04
> **pikpok said:**
> ... type **update-grub** in OS, which have GRUB installed.

```
sudo update-grub
```... actually. ;)

Do that in the OS that is booting, Lubuntu. Sounds like Lubuntu was controlling grub and the upgrade killed it. This should fix it.

---

