---
title: "&quot;Input Signal Out Of Range'' Help A Newbie Out!"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by blair :D on 2009-11-27
Hi, I'm New To Ubuntu. And I Can only run it on my netbook.  But when i try to boot it on my pc via the live CD, after the white ubuntu logo things pops up on the screen with the  black background, My monitor displays the message "Input Signal Out Of Range" I'm not sure what this means, but i have tried a few suggestions...

I'm running XP SP3 On the computer and the i368 version of ubuntu is what i am trying to install, i have an nvidea gforce 6800 graphics card.

Can anyone help me out so i can start using ubuntu?

Any help would be great!!

---

### Post by cariboo on 2009-11-27
What you are seeing means that the horizontal sync and vertical refresh rates are set wrong. What type of graphics adapter and monitor do you have?

---

### Post by blair :D on 2009-11-28
I Have a COMPAQ FP5315 Monitor, and an Nvidea gforce 7600.

---

### Post by blair :D on 2009-11-29
Shameless Bump...

---

### Post by Vantrax on 2009-12-17
If you can hit Ctrl Alt F1 and log in run:

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start


That should fix things most of the time

If it doesnt you need to install envyng-core from the command line and use that to install the driver for you.

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
Installing the driver in the live environment won't do a lot of good.

---

### Post by theozzlives on 2009-12-17
> **ST3ALTHPSYCH0 said:**
> Installing the driver in the live environment won't do a lot of good.

True, you using Karmic? I had problems with my nVIDIA 6 series with Karmic.

---

### Post by lidex on 2009-12-18
You could try booting with safe graphics mode. I believe it's F4 at the LiveCD boot menu.

---

### Post by ukripper on 2009-12-18
When you reach login screen just press CTRL + ALT + F1 and a black screen will become available for you to type login(username) and your password. After puting your username and password follow my posts #7 and #9 in this thread - [http://ubuntuforums.org/showthread.php?t=1329428](http://ubuntuforums.org/showthread.php?t=1329428)

it will give you your horizonatl and vertical refresh rates.

---

