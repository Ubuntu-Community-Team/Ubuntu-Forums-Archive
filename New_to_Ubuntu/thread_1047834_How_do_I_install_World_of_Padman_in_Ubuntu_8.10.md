---
title: "How do I install World of Padman in Ubuntu 8.10?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-22
Urghh. I downloaded World of Padman and I can't install it! I can't find out how... I've been trying for like 20 minutes. Can someone tell me what to do? 

Thanks.

---

### Post by emarkd on 2009-01-22
Not sure as I've never used it.  I was gonna download it and check it out for you but it's quite large.  As an option, though, I see that there's a packaged .deb for the game at [http://www.getdeb.net/app/World+Of+Padman]("http://www.getdeb.net/app/World+Of+Padman")

---

### Post by gymophett on 2009-01-22
> **emarkd said:**
> Not sure as I've never used it.  I was gonna download it and check it out for you but it's quite large.  As an option, though, I see that there's a packaged .deb for the game at [http://www.getdeb.net/app/World+Of+Padman]("http://www.getdeb.net/app/World+Of+Padman")
 
Thanks so much. That website will come in handy ;)

---

### Post by emarkd on 2009-01-22
you're welcome.  if you'd prefer to access .debs from that source using synaptic or aptitude instead of having to download and install, see [this guide]("http://ubuntuforums.org/showthread.php?t=632722").

---

### Post by gymophett on 2009-01-22
> **emarkd said:**
> you're welcome.  if you'd prefer to access .debs from that source using synaptic or aptitude instead of having to download and install, see [this guide]("http://ubuntuforums.org/showthread.php?t=632722").

You've saved me tons of hell. I'm somewhat new to Linux and hate compiling and stuff.

Thanks so so much. :)

---

### Post by emarkd on 2009-01-22
compiling from source has it's place, but for most purposes prebuilt packages are the way to go -- if you can find them.  i'm glad i could point you in the right direction.

---

### Post by paradroid90 on 2009-05-05
Hi hope someone can help!!!

I need to move the World of Padman pad.pak folder into the file system folder to play the maps every time i try by moving the folder via drawer in the desktop i keep getting that i dont have access.....can anybody help

---

### Post by geostrydar on 2009-05-13
> **paradroid90 said:**
> Hi hope someone can help!!!

I need to move the World of Padman pad.pak folder into the file system folder to play the maps every time i try by moving the folder via drawer in the desktop i keep getting that i dont have access.....can anybody help

The destination is owned by root and you need to use root privileges to write to it. If you want to use Nautilus, you need to open it as root. Open a terminal and type the following:

```
gksudo nautilus
```

Nautilus will open to the root home folder where you can navigate to the destination you are looking for, with root writable privileges. Now you can drag and drop what you need.

---

