---
title: "would like to setup triple boot"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-12-30
i have ubuntu netbook remix and windows 7 installed.  i would like to add moblin to the fold.  i was wondering whether or not when you install it if moblin will detect other operating systems?

---

### Post by tom.swartz07 on 2009-12-30
> **mamamia88 said:**
> i have ubuntu netbook remix and windows 7 installed.  i would like to add moblin to the fold.  i was wondering whether or not when you install it if moblin will detect other operating systems?

Im not sure about the install methods of Moblin, but I do know that if you use a LiveCD install of the system, and select 'install side-by-side' it will automatically partition your system and update your bootloader to recognize it.
I only say this because Jolicloud - another netbook based OS, uses WUBI, a Windows based installer.


Hope this helps!

---

### Post by mamamia88 on 2009-12-30
cool thanks i am running from live cd now and i ilke what i see and think i will give it a go

---

### Post by mamamia88 on 2009-12-30
ok i set it up but all grub says is moblin and other.  other boots windows 7.  i know ubuntu is still intact because i schrunk the partiton to make room for moblin.  can someone give me some instructions on how to add it back to my menu.lst

---

### Post by tom.swartz07 on 2009-12-30
> **mamamia88 said:**
> ok i set it up but all grub says is moblin and other.  other boots windows 7.  i know ubuntu is still intact because i schrunk the partiton to make room for moblin.  can someone give me some instructions on how to add it back to my menu.lst

This is arguably the best method to restore grub. You'll need a live version of Ubuntu.
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by wilee-nilee on 2009-12-30
> **mamamia88 said:**
> ok i set it up but all grub says is moblin and other.  other boots windows 7.  i know ubuntu is still intact because i schrunk the partiton to make room for moblin.  can someone give me some instructions on how to add it back to my menu.lst

Which Ubuntu is installed if it is Karmic or beyond or you have grub2 the post above should be the answer. If you have the Jaunty UNR then another grub is involved.

---

### Post by mamamia88 on 2009-12-30
karmic netbook remix

---

