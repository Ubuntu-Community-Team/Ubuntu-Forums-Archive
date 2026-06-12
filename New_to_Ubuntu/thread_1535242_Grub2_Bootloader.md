---
title: "Grub2 Bootloader"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by kepps03 on 2010-07-20
Is there a way to delete Grub 2 and use only Windows 7/Vista loader on a multi boot system? I like windows boot loader leaps and bounds more and I would love to be able to use it without grub 2. I delete it b4, but was unable to load Ubuntu without it. Is it even possible to delete grub 2 and use windows boot loader to load Ubuntu.
 
 
-My version is Ubuntu 10.04 LTS (32bit)(gnome)
 
 
Please keep your replies nice. I'm new to Ubuntu and I don't know where to start. Yes! A noob! So please respect me and I'll do the same.

---

### Post by jtarin on 2010-07-20
[EasyBCD]("http://neosmart.net/forums/showthread.php?t=642") is what your looking for. It allows you to edit the Win7/Vista bootloader and have it boot Grub2 on the / of your Linux partition.You must reinstall Grub2 to the / of your Linux partition.

---

### Post by lolzwut on 2010-07-20
EasyBCD will re install the mbr for win

---

### Post by jtarin on 2010-07-21
Yes if you can get into Win to install it.

---

### Post by kepps03 on 2010-07-21
> **jtarin said:**
> [EasyBCD]("http://neosmart.net/forums/showthread.php?t=642") is what your looking for. It allows you to edit the Win7/Vista bootloader and have it boot Grub2 on the / of your Linux partition.You must reinstall Grub2 to the / of your Linux partition.
 
 
I'm a Ubuntu n00b! Can you tell me how to reinstall Grub2 to / and what setting I need in EasyBCD 2.0? Thanks in advance!

---

### Post by jtarin on 2010-07-21
> **kepps03 said:**
> I'm a Ubuntu n00b! Can you tell me how to reinstall Grub2 to / and what setting I need in EasyBCD 2.0? Thanks in advance!
[Go to this page]("https://help.ubuntu.com/community/Grub2") and scroll wayyyyy down the page to the topic heading **_Reinstalling GRUB 2_**It will guide you through the reinstalltion of Grub2. Bookmark for later reference.
As for Easy BCD...go here and follow the instructions for "Vista before Linux". Using the link I gave you above Make sure you down load version 2.0 of EasyBcd as this includes the option for Grub2 as well as Legacy Grub. You will want to use Grub2. It says Vista but will work fine on Win7 as well.

---

### Post by kepps03 on 2010-07-22
> **jtarin said:**
> [Go to this page]("https://help.ubuntu.com/community/Grub2") and scroll wayyyyy down the page to the topic heading **_Reinstalling GRUB 2_**It will guide you through the reinstalltion of Grub2. Bookmark for later reference.
As for Easy BCD...go here and follow the instructions for "Vista before Linux". Using the link I gave you above Make sure you down load version 2.0 of EasyBcd as this includes the option for Grub2 as well as Legacy Grub. You will want to use Grub2. It says Vista but will work fine on Win7 as well.



Thanks! You deserve a hand full of beans! lol.

---

### Post by jtarin on 2010-07-22
> **kepps03 said:**
> Thanks! You deserve a hand full of beans! lol.

Forgot to insert links for EasyBCD
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
but for EasyBCD 2.0 there will be a tab for Grub2 and Grub legacy....you want Grub2. As I said instructions for Vista are identical for Win7.

---

### Post by kepps03 on 2010-07-22
> **jtarin said:**
> Forgot to insert links for EasyBCD
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
but for EasyBCD 2.0 there will be a tab for Grub2 and Grub legacy....you want Grub2. As I said instructions for Vista are identical for Win7.


I used EasyBCD b4. I got that program already. Thanks so much for being thorough.

---

