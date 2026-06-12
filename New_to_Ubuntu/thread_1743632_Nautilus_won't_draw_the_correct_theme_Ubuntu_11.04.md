---
title: "Nautilus won't draw the correct theme Ubuntu 11.04"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by loukingjr on 2011-04-29
I installed Ubuntu 11.04 in VirtualBox 4.0.6 and nautilus refuses to draw the correct theme...
okay here is the problem I'm having...
[IMG]https://lh5.googleusercontent.com/_sA9c938TUEU/TbsqGWPkxOI/AAAAAAAAHMQ/z1bKlrylklg/s400/screenshot_01.jpg[/IMG]

as you can see nautilus won't draw anything but the root theme no matter which theme I choose.

---

### Post by loukingjr on 2011-04-29
ok, not sure why but every time I boot or reboot Ubuntu 11.04 I have to run these commands and it works...
louis@louis-VirtualBox:~$ killall -9 gnome-settings-daemon && gnome-settings-daemon
louis@louis-VirtualBox:~$ killall nautilus && nautilus

kind of annoying really.

---

### Post by zebrattt on 2011-05-02
> **loukingjr said:**
> ok, not sure why but every time I boot or reboot Ubuntu 11.04 I have to run these commands and it works...
louis@louis-VirtualBox:~$ killall -9 gnome-settings-daemon && gnome-settings-daemon
louis@louis-VirtualBox:~$ killall nautilus && nautilus

kind of annoying really.

nautilus is not working properly in ubuntu 11.04.  i have a draw desktop problem too.

---

### Post by nvjopsddhapnv on 2011-05-04
Nautilus is not working. When I click Places>Home or Places>Desktop or Places>Documents or Places>Downloads or any other bookmark (except Places>Computer) instead of opening the desired window I ended with a VLC screen showing the bookmark places in the playlist window. However, when I run the command Alt+F2 then run nautilus, then it works fine.
What is wrong I do not know?
Can anyone help me!! :)

---

### Post by migs73 on 2011-05-04
> **chemrajib said:**
> Nautilus is not working. When I click Places>Home or Places>Desktop or Places>Documents or Places>Downloads or any other bookmark (except Places>Computer) instead of opening the desired window I ended with a VLC screen showing the bookmark places in the playlist window. However, when I run the command Alt+F2 then run nautilus, then it works fine.
What is wrong I do not know?
Can anyone help me!! :)

Browse to a folder (places>computer you say works) right click on it and select 'open with other application'. Browse the list and select 'File Browser' then check the box at the bottom of the window that says something like 'always use this for 'folder' type file' or somthing like that. then click open.

Then try your places menu again.

OP

I sometimes get the wrong theme on 10.10 as well, maybe not a natty problem?

---

### Post by nvjopsddhapnv on 2011-05-05
Thanks a lot **migs73**. It solves the problem. Thanks again.

---

### Post by unadulterated on 2011-06-11
I have been having this problem of nautilus not loading in the current theme (but with the most basic theme, infact the same one in the image in the start of this post). I am using ubuntu 11.04, initially it was working properly but not its not. any permanent solution known would be helpful.

---

### Post by wildmanne39 on 2011-06-11
> **unadulterated said:**
> I have been having this problem of nautilus not loading in the current theme (but with the most basic theme, infact the same one in the image in the start of this post). I am using ubuntu 11.04, initially it was working properly but not its not. any permanent solution known would be helpful.Hi, if you have the same desktop as the picture in the first post you are not booting to unity it is booting to ubuntu classic. Go into additional drivers and see if you have a driver for your video card there and activate it.

---

