---
title: "Where's what I've installed"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by oopsie on 2010-03-18
If I install something using the Synaptic package manager, and it doesn't appear to have turned up in any of the menus, where is it and how do I run it?

---

### Post by pablolie on 2010-03-18
> **oopsie said:**
> If I install something using the Synaptic package manager, and it doesn't appear to have turned up in any of the menus, where is it and how do I run it?

What is it you installed? And what Ubuntu version?

---

### Post by wjm on 2010-03-18
Anything you install from Synaptic that is not a library, source code or codec will most definitely show up in the Gnome/KDE/XFCE application menus.

---

### Post by oopsie on 2010-03-18
9.04

I tried installing a few things like a checkers game, but it didn't turn up in any menus as far as I could see.

I also tried installing Hatari, but no luck there either, which is kinda annoying since I've got it on Windows. The windows one is a later version too than the one I saw in the Synaptic package manager

---

### Post by the yawner on 2010-03-18
What exactly did you tried to install?

---

### Post by dineshs on 2010-03-18
You can use a launcher in case it is not listed under different menus
[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

---

### Post by the yawner on 2010-03-18
Whoops, my reply wasn't fast enough. Sorry for appearing to repeat the question already asked.

Typical desktop programs add a *.desktop file on this... particular location (Don't have an Ubuntu box to verify) which in turn should automatically add the installed program on the menu.

---

### Post by trideceth12 on 2010-03-18
I have had this same problem several times... most recently with the program "knights" which is a FICS client, but many times before that too.

Usually I just run it from terminal (Open a terminal window and type knights) or create a launcher to do the same, but I would like to know how to add these programs to the application menu.

---

### Post by dineshs on 2010-03-18
I think this is the procedure
go to system-preferences-main menu
select the main menu where you want the application to be listed, and on right side click new item
fill the details especially the command,click on the icon to select a good icon ,then click OK

---

### Post by dineshs on 2010-03-18
> **oopsie said:**
> 9.04

I also tried installing Hatari, but no luck there either, which is kinda annoying since I've got it on Windows. The windows one is a later version too than the one I saw in the Synaptic package manager
To create a launcher on desktop,right click on the desktop and click create launcher.
Type is application
Name you can give hatari
in the command field type ```
hatari
```case sensitive
Give any comment you like
click on the icon if you want to change the default icon
click OK

---

### Post by oopsie on 2010-03-18
> **dineshs said:**
> I think this is the procedure
go to system-preferences-main menu
select the main menu where you want the application to be listed, and on right side click new item
fill the details especially the command,click on the icon to select a good icon ,then click OK

Thank you.

This worked

---

### Post by trideceth12 on 2010-03-18
> **dineshs said:**
> I think this is the procedure
go to system-preferences-main menu
select the main menu where you want the application to be listed, and on right side click new item
fill the details especially the command,click on the icon to select a good icon ,then click OK

Great! I learned something new.:D

---

