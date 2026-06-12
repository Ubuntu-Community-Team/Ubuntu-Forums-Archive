---
title: "Modifying ubuntu-desktop to start in console mode"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by coverslide on 2009-10-28
OK, so I have a three-part question.

First, installed ubuntu-desktop, but I prefer it to start in console mode, ie without X/gdm/etc., so I would like to know where and how to modify the settings so that it would start in console mode. 

Also, how would I make this into a grub menu command in case I would like to choose between the two. 

Third, would it be possible to have a special shutdown command that sets grub to load either console or desktop mode on the next boot?

Thank you very much for your help.

---

### Post by Tyke91 on 2009-10-28
you want to look for guides about disabling gdm by default.

You can find the script that starts it in /etc/rc2.d but I REALLY wouldn't mess with that. 

I don't know if grub would do it or not. I'm going to guess no.

---

### Post by JBAlaska on 2009-10-28
This [Thread](http://ubuntuforums.org/showthread.php?t=349517) will do what you want:

---

### Post by anewguy on 2009-10-28
Read up on run levels, then I think you'll find what you want.

dave :)

---

