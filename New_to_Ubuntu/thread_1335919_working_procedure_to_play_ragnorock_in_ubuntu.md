---
title: "working procedure to play ragnorock in ubuntu??"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by ashu. on 2009-11-23
can any one tell me working procedure to play ragnorock in ubuntu?? i went downloading n i got crazy coz no client file opens i use ubuntu 9.04. plz tell me procedure to install n play online...
can u also tell me other client based online games supporting linux os

---

### Post by ashu. on 2009-11-24
plz y any 1 wont reply this is not the first time almost this is 5th time no one replies to my query plz help me i've done no crime plz help

---

### Post by 3rdalbum on 2009-11-24
I'm sorry, probably nobody here knows of this program.

Can you please say clearly what you have already tried doing to get this program to work? Are there instructions included with the file you downloaded?

---

### Post by dependancyhell on 2009-11-24
I believe this is what you're looking for [http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928)

---

### Post by ashu. on 2009-11-24
> **3rdalbum said:**
> I'm sorry, probably nobody here knows of this program.

Can you please say clearly what you have already tried doing to get this program to work? Are there instructions included with the file you downloaded?
this is a online client based game which needs a client to run which i downloaded but cannot run

---

### Post by gackt on 2009-11-24
Hi there, 

First of all, ragnarok is online game which is window-xp base so you could not get this game run by simply clicking the game. 

You might want to try wine, after you install the game run the game trough terminal so when the ragnarok couldn't start you still can read the error on the console. If the error was dll missing or something like then the workaround is to copy the dll to windows folder (in your ubuntu wine directory). 

hey why you dont try this instead, and skip the headache:

[http://www.playonlinux.com/](http://www.playonlinux.com/)

---

### Post by MelDJ on 2009-11-24
install xp or whatever win into virtualbox and play there?

---

### Post by mvalviar on 2009-11-24
Open Applications>Accesories>Terminal and type ```
sudo apt-get install wine
```.

Now if you have the install disc the autorun should work when you insert that in your disc drive.

If you downloaded the install files. Just double click on the setup.exe or install.exe and it should install. If you're getting the archive manager when double click on install/setup.exe right click on it and select open with>wine program loader.

Once installed the program is available under Applications>Wine>Programs>Ragnarok.

If you run the program you should be able to reach the login prompt but here's the catch: Game Guard will not allow you to play. You need to find a hexed Ragnarok.exe that has Game Guard disabled. Replace the file ~/.wine/drive_c/Program Files/Gravity/Ragnarok Online/Ragnarok.exe with that hexed Ragnarok.exe. Too see the .wine folder go to your home folder and press Ctrl-h.

This is the procedure I used to play Ragnarok on ubuntu before.

---

