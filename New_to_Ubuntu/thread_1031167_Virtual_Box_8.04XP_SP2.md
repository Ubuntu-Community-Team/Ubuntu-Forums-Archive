---
title: "Virtual Box 8.04/XP SP2"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by dinomite89 on 2009-01-05
Hiya All,

i just installed virtual box on my Linux and am wanting to see if it is possible to play games through it, (therefore eliminating my uses for windows) i have successfully installed XP and i insert a game disc, which happened to be assassins creed, i try to open the disc and i get a error saying parameter is incorrect, does anyone know how to fix tis problem or am i trying to do something that virtual box is not supposed to??? any help would be great

---

### Post by carml on 2009-01-05
You have to enable the cd/dvd rom in general settings,which you get when you select your virtual machine. :D

---

### Post by bluefrog on 2009-01-05
you are not bypassing the need of windows, just bypassing the need of physical hardware for windows.

you try to read a legit CDROM from inside virtualized windows? There is no reason for the CDROM not to be opened. (except maybe for some kind of protection which would prevent you, but it sounds strange.)

---

### Post by theozzlives on 2009-01-05
The only problem I've had with VirtualBox is the Virtual Video doesn't support OpenGL.

---

### Post by ubersolid on 2009-01-05
Virtualbox 2.1 supports opengl in xp / vista guests.

---

### Post by dinomite89 on 2009-01-05
yeah thats what ive done the cd shows up in the VB my computer its only when i try to open it i get the Peramteres Incorrect message

---

### Post by dinomite89 on 2009-01-05
Ok rebooted and now i ant even get it to read, i sez assins creed dvd but shows no icon and keeps asking me to insert a dvd when i try to open it or the autrun tries to kick in

---

### Post by howefield on 2009-01-05
Don't know if it would work, but you could try making an .iso of the cd and mounting the iso.

---

### Post by dinomite89 on 2009-01-05
Okay well the iso worked but the game fails to run, i just dont think its ment ot run on virtual box, i might give wine ago instead, somthing about audio driver is alerady in use, thank you for your help

---

### Post by howefield on 2009-01-05
Assassins Creed (version 1) gets a bronze in the wine apps database. So it looks like it might work..

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11069&iTestingId=22141](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11069&iTestingId=22141)

---

