---
title: "View my entire hard drive?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by SmoothFreeze on 2009-03-05
Hi i just installed Ubuntu using Wubi... Now i am in Ubuntu and i cant find my files and folders which is my Windows side? I want to copy and paste some of my music to my Ubuntu.

---

### Post by sazan on 2009-03-05
just open any explorer and you will see your disks there, double-click to mount.
You can also mount those drives using terminal ->

mount <disk> /media

---

### Post by albandy on 2009-03-05
what kind of installation? repartitioning or inside windows folder with wubi?
if wubi, it's mounted on /host so you don't need to mount it again, else do it as "sazan" said

---

### Post by yther on 2009-03-05
You should have a folder in your main file system called "host"—everything from your main Windows drive should be in there.

Here's an example:  [Click!]("http://www.comp-sos.com/compsosimg/Wubi/image046.png")

---

### Post by SmoothFreeze on 2009-03-05
I installed using Wubi in Windows. Now i want to find my files which is my Windows xp, but i cant find it. When i clicked places>computer, i see my drives but when i clicked my hard drive, i cant find my files and folders. All i founds i my Ubuntu related files

---

### Post by SmoothFreeze on 2009-03-05
Ok thanks yther i found it lol.

---

### Post by SmoothFreeze on 2009-03-05
1 more qn, how do i make a shortcut of my hard drive to my desktop?

---

### Post by albandy on 2009-03-05
right click on desktop.
new launcher
in the command section type: nautilus /host

or

right click
new launcher
change option to place
and select the destination

---

