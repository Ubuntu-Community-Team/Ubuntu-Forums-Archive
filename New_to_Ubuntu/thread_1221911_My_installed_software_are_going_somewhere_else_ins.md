---
title: "My installed software are going somewhere else instead of in my applications"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Kanval87 on 2009-07-24
it's my first experience with ubuntu and i started liking it though sometimes it makes things harder to understand for instance. i installed ubuntu 9.4 on my another system and it is not getting the graphic driver. my another system is intel 28 HT with intel 865gvxz motherboard. since it was'nt really helping me with things so i switched to 8.04 and here i m facing another problem it's like i ca'nt access the application i installed from synaptic package installer. in other words it's acting picky since it is showing some installed files such as avidemux but it is not showing application such as kdenlive. since i m a nump some indepth help would b appreciated thanks in advance

---

### Post by jerrrys on 2009-07-24
Hi Kanval87:

I downloaded this kdenlive just to see what the deal was...and your right, it does not show up in the menu.  so here's a work around...

go to  Home>File System>usr>bin>kdenlive and...

right click on kdenlive and copy.  then go back to your home folder and paste

you can now double click on this (in your home folder) and it will open

don't know why this has to be, should just appear in the menu.  maybe someone else thats in the know will come along and tell us...

---

### Post by CatKiller on 2009-07-24
Intel graphics do not have a proprietary driver, which is why you won't find one listed in the tool that finds proprietary drivers.

Kdenlive is a KDE application. You'll get a menu entry if you're using KDE. You can just create your own menu entry (right-click on menu and select Edit Menus) with the command **kdenlive**. If you want to add the same comment that the KDE menu entry has, it's > Nonlinear video editor for KDE

---

### Post by Kanval87 on 2009-08-24
thanks sir...it helped :)

---

