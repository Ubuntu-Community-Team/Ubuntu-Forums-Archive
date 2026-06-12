---
title: "blank screen with mouse cursor at boot?!"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by stolle on 2011-02-25
started with an install of 8.04 then upgraded to 10.04 rebooted a few times and everything was fine. I installed Klam-av, and turned the computer off, when i turned it back on it will not boot into a gui. all i get is a black screen with a mouse cursor, if i "<ctrl><alt><delete>" it pops up "xscreensaver" and asks for a password when i enter the password it does nothing but run the screensaver and or goes back to a black screen?

i can hit <ctrl><alt><F2> and use the command line just fine just no gui.

i dont have a problem with just reinstalling but this is driving me nuts i want to know why it did this? i did some searching around but didnt find anything.

---

### Post by vivek.pandey on 2011-02-25
> **stolle said:**
> started with an install of 8.04 then upgraded to 10.04 rebooted a few times and everything was fine. I installed Klam-av, and turned the computer off, when i turned it back on it will not boot into a gui. all i get is a black screen with a mouse cursor, if i "<ctrl><alt><delete>" it pops up "xscreensaver" and asks for a password when i enter the password it does nothing but run the screensaver and or goes back to a black screen?

i can hit <ctrl><alt><F2> and use the command line just fine just no gui.

i dont have a problem with just reinstalling but this is driving me nuts i want to know why it did this? i did some searching around but didnt find anything.


have you tried typing startx in the command line . you will get a gui

---

### Post by Jose Catre-Vandis on 2011-02-25
Also try recovery mode it will offer you some choices and you get a better lok at what is happening. Sounds like X is doing something but not everything....

Oh, and you are not running an openbox session ? I guess you have tried a right click on the desktop?

---

### Post by hansolo4949 on 2011-02-25
Well, if Klam is messing up your boot, and since you have acces to a terminal, open it up and type: sudo apt-get remove Klam-av. That should fix it!

---

### Post by stolle on 2011-02-26
thank you for the replys, i tryed startx theres an error say its already running. i will try the other suggestions when i get back to work on monday. thanks!

---

### Post by stolle on 2011-03-01
tryed all of the above, nothing worked, looks like im reinstalling, thanks everyone!

---

### Post by lastguy on 2011-03-02
> **stolle said:**
> tryed all of the above, nothing worked, looks like im reinstalling, thanks everyone!

it seems grub2.conf problem there are "closed" topic.

---

