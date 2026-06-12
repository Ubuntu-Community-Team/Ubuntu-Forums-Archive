---
title: "Running flash .exe animations"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by evilkastel on 2008-12-13
Hi there. I have to run some flash animations for a college paper, they are in .exe. also, inside a folder is a .swf. how cold i acces the content? I'm desperate, i need to access that. any help appreciatted.

---

### Post by jbrown96 on 2008-12-13
Not sure what to do with the exe's, but you should be able to play the .swf with vlc. ```
sudo apt-get install vlc
```

---

### Post by adobrakic on 2008-12-13
Flash doesn't come in .exe, unless its a program that plays flash.
Open the .swf in firefox or VLC.

---

### Post by evilkastel on 2008-12-13
.swf won't open with vlc or firefox (i had tried those already). any toughts?

---

### Post by Tom--d on 2008-12-13
Install Wine and see if it runs. If not, just drag the file in a new tab in Firefox.

---

### Post by mgmiller on 2008-12-13
I just tried a few .swf file I have lying around, they all play in firefox, assuming you have the flash plugin installed.  

If you don't it's part of the ubuntu-restricted-extras package, assuming you are running ubuntu rather than kubuntu or xubuntu.

I also have a flash that runs as an .exe and the only way to make it work is with wine.

---

### Post by Izek on 2008-12-13
> **adobrakic said:**
> Flash doesn't come in .exe, unless its a program that plays flash.

It's called a **Flash Projector**, Flash MX and above can export as an exe (Projector) file so that people do not need to have flash installed. It's a rather clunky method nowadays though. Director (now defunct) could do the same thing.

---

### Post by adobrakic on 2008-12-13
[http://ubuntuforums.org/showthread.php?t=298871](http://ubuntuforums.org/showthread.php?t=298871)

---

### Post by evilkastel on 2008-12-13
mozilla won't open it. if someone could point how can i run it on wine i'll be very thankful.

---

