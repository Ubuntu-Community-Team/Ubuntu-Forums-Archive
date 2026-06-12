---
title: "[SOLVED] Moving or removing entries in grub"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by CageUK on 2008-12-14
Is it within a newbies scope to edit Grub to move and remove existing entries in a dual boot system?

I have duplicate Ubuntu entries due to an aborted installation and I would like to move my Vista boot option to the top of the list.

A couple of the threads I've read look pretty complicated but I'm willing to give it a go.

Cheers

---

### Post by albinootje on 2008-12-14
(1)
Edit /boot/grub/menu.lst

First of all make sure that the line with :

default         0

really uses 0 and no other number

(2)
Then find the section with examples :

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1

(3)

Find the section about Vista, and copy and paste that
right under that example, so it looks something like this :

title         Windows Vista
root          (hd0,0)
makeactive
chainloader   +1

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

That should be enough. :)

---

### Post by drs305 on 2008-12-14
Take a look at StartUp-Manager - a gui-based menu.lst tweaker. It can set the default OS without moving anything around. It won't delete double entries, although it does have options to limit the number of kernels to display.

Even though it won't do both things you are asking for currently, it is a great app and provides a very safe way to tweak grub's menu.lst

Here is a tutorial link for StartUp-Manager. It also includes some tips for manually editing menu.lst:
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by CageUK on 2008-12-14
Brilliant.

Between the two posts I got exactly what I wanted to achieve.

Thanks guys :)

---

