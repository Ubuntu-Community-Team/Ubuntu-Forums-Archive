---
title: "i cant belive this virus like behavior in linux????"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by ashu. on 2009-11-17
hi this is a hurting but true experience of mine i came across a file in USB mass storage device of my friend which i tried to delete it made multiple copies with names of files in my desktop with .exe extention.it had created many .exe processes which i couldnt kill without manually pulling out the device off usb port i have archived the virus like file.hoping some one here can better linux from these headache

---

### Post by whoop on 2009-11-17
So, where is the file? I would like to take a look...

---

### Post by mister_p_1998 on 2009-11-17
Yeah, Ive had that one, it only copies itself on windows, you have to run nautilus as root to delete it.

---

### Post by ashu. on 2009-11-17
this is the archived file its renamed .txt n archived sorry i hadnt attached the file in my last post

---

### Post by undecim on 2009-11-17
Maybe instead of deleting it, you accidentally ran it in Wine?

---

### Post by ukripper on 2009-11-17
> **undecim said:**
> maybe instead of deleting it, you accidentally ran it in wine?

+1 definitely sounds the case. Wine can be the only program here which would propagate .exe like that on linux based system.

---

### Post by DGortze380 on 2009-11-17
> **ukripper said:**
> +1 definitely sounds the case. Wine can be the only program here which would propagate .exe like that on linux based system.

x2 sounds very much like it ran in WINE.

I doubt any serious damage was (or even could have been) done. Just gain root privileges and delete it.

---

### Post by undecim on 2009-11-17
If I were you I would delete my .wine directory from my home directory (though this will require you to reinstall any wine applications you have) and search your Desktop, Documents, Pictures, Music, etc. folders for any .exe files.

---

### Post by ukripper on 2009-11-17
> **undecim said:**
> If I were you I would delete my .wine directory from my home directory (though this will require you to reinstall any wine applications you have) and search your Desktop, Documents, Pictures, Music, etc. folders for any .exe files.

and also get rid of wine completely just in case.

---

### Post by ashu. on 2009-11-17
ya thanks i have no use for wine now i had installed only for the sake of completion of my project thanks i'm happy to know there is no threat

---

### Post by openuniverse on 2009-11-17
.

---

### Post by Paqman on 2009-11-17
> **ashu. said:**
> i'm happy to know there is no threat

Any virus that was propagating itself through Wine would be contained to your /home folder and the fake Windows file structure contained there. It would have no real access to real system resources, so you could always beat it by nuking Wine.

---

