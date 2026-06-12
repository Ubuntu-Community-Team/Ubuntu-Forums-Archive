---
title: "Startup problems, boots into non-graphical environment."
date: 2011-07-02
forum: New to Ubuntu
---

### Post by MollyWop on 2011-07-02
This is what happens when I boot into my somewhat old pc dual booted with XP and Ubuntu. (This issue might be factored by a NVIDIA graphics card.)

I boot into Ubuntu, with Linux 2.6.35-30 generic

black screen comes on with alot of text saying something about NVIDIA at times and a bunch of other stuff that is hard to read.

Then it gets to a screen that says Ubuntu 10.10 Ubuntu tty1 (I named my computer ubuntu so its basically telling me Ubuntu 10.10 *your computer name*)
Ubuntu login: eth1 no IPv6 routers present
Login:

when I login it will tell me 11.04 is available and gives me the regular Mike@Ubuntu:~$
I try "sudo service gdm start" and sometimes it will send me to the desktop and sometimes it will just say process "whatever process number" is already running. and will give me nothing to do but reboot. What can I do to fix this? Thank you.
EDIT: and other times it will tell me > 4.574053 XGIfb: Mode 'none' not supported anymore. using default
From there I have to reboot and try my luck again.

PS  I just updated my graphics card from the default Ubuntu repo to the official sites driver download.

---

### Post by haqking on 2011-07-02
[I]try pressing alt + f7 for the gui.

if it is not started.

try startx

or this to restart it

[I]sudo /etc/init.d/gdm restart

or this to start if it never started at all

[/I]*sudo /etc/init.d/gdm start*[/I]

---

### Post by MollyWop on 2011-07-02
> **haqking said:**
> [I]try pressing alt + f7 for the gui.

if it is not started.

try startx

or this to restart it

[I]sudo /etc/init.d/gdm restart

or this to start if it never started at all

[/I]*sudo /etc/init.d/gdm start*[/I]
the thing is that that will only temporarily solve the problem. how do i make it so that it will boot normally.

---

### Post by haqking on 2011-07-02
try

dpkg-reconfigure gdm

---

### Post by wildmanne39 on 2011-07-02
Hi, go to this link and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

