---
title: "New Install Problem"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by sailworkless on 2009-08-28
I'm trying to get 9.04 up and running on an old,old box (Dell Dimension L733r - it's a P3 at 733MHz). The install works fine (albeit a bit slow). All the basics work - Firefox,OpenOffice,etc. 

The problem comes when I try to install anything new (Updates through the update manager, flash, etc). When I try to do this, the screen gets dim (shadow effect) and a white box pops up. No text or anything in the box. The machine then freezes up and nothing happens. I've tried letting it sit overnight, just to see if it's running something really slowly. I can almost always get back to the OS by pressing escape. From there, everything still works fine.

Any ideas as to the problem and/or solution? Could it have anything to do with the silly integrated graphics on this box? Or could this box be just to old to work?

Thanks for any help,
Sail

---

### Post by LewRockwell on 2009-08-28
too old really, but if it's packed full of ram it might limp along

.

---

### Post by blueridgedog on 2009-08-28
I would try xubuntu or mint or puppy on that box.

---

### Post by Katalog on 2009-08-28
Have you tried installing a lighter distribution? Crunchbang is based off Ubuntu but uses Openbox for the WM, so your older machine might be able to cope with it better than a straight Ubuntu install. The learning curve for Openbox is probably a bit steeper (but not by much) than GNOME, but it might be worth your trouble.

---

### Post by natravis on 2009-08-28
As an aside, I also agree with the other posters that you should install a more lightweight distribution. Xubuntu, mint, and puppy linux are all excellent choices though I only have personal experience with the first.

Back to your question, the box that is popping up is asking for your root password so that it can install things. A temporary workaround would be to use the Terminal to input this

```
sudo apt-get update
sudo apt-get upgrade
```

to update the currently installed packages and you could install new programs via

```
sudo apt-get install NAMEOFPROGRAM
```

but that is not guaranteed to work because the package name is not always the same as what shows up in the title bar. I would suggest checking to see if there is a particular graphics driver you can enable. You can access that via System->Administration->Hardware Drivers. I had to install my Nvidia drivers from there to use some features of my computer (like the flashy-ness of Compiz).

---

### Post by sailworkless on 2009-08-29
Thanks All,

I'll give XUbuntu a try.

Sail

---

### Post by Katalog on 2009-08-29
> **natravis said:**
> As an aside, I also agree with the other posters that you should install a more lightweight distribution. Xubuntu, mint, and puppy linux are all excellent choices though I only have personal experience with the first.

But isn't Mint pretty much just straight Ubuntu, only with even *more* stuff added to it? I had it installed for a few weeks at one time and aside from some out of the box functionality that you don't get with Ubuntu (you have to install the same stuff manually) and some Mint-specific applications, it seemed just like any other Ubuntu install to me (only more green :P).

---

### Post by halitech on 2009-08-29
I've installed on older machines with Debian using the instructions here

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by k5corral on 2009-08-30
You never mentioned how much ram (memory) is installed on your Dell.  If you have less than 256mb, then there's your problem. You can find used 256mb sticks online or at a local repair shop for as little as $7 each, and they are easy to install. Pop in 2 and you'll be good to go with most distros.

---

### Post by 3rdalbum on 2009-08-30
> **sailworkless said:**
> I'm trying to get 9.04 up and running on an old,old box (Dell Dimension L733r - it's a P3 at 733MHz). The install works fine (albeit a bit slow). All the basics work - Firefox,OpenOffice,etc. 

The problem comes when I try to install anything new (Updates through the update manager, flash, etc). When I try to do this, the screen gets dim (shadow effect) and a white box pops up. No text or anything in the box. The machine then freezes up and nothing happens. I've tried letting it sit overnight, just to see if it's running something really slowly. I can almost always get back to the OS by pressing escape. From there, everything still works fine.

Any ideas as to the problem and/or solution? Could it have anything to do with the silly integrated graphics on this box? Or could this box be just to old to work?

Thanks for any help,
Sail

It seems that this white box is actually the "gksudo" prompt - it's the secure box that allows you to enter your password to elevate a program to root (which is necessary for using the update manager or installing anything).

I have no idea why it's not drawing correctly. It could be some sort of graphics issue. But if you type your password at this point and hit the Enter key, the box should go away and the program will run. I'd definitely suggest running the system updates, because there are some small Intel driver updates that might get rid of the problem; Intel is rewriting their graphics driver at the moment and there are some known graphical artifacts, although I haven't heard of this particular one before.

---

### Post by Bartender on 2009-08-30
> **k5corral said:**
> You never mentioned how much ram (memory) is installed on your Dell.  If you have less than 256mb, then there's your problem. You can find used 256mb sticks online or at a local repair shop for as little as $7 each, and they are easy to install. Pop in 2 and you'll be good to go with most distros.

+2

I've got an old PIII/1GHz desktop PC with about 750 MB RAM in it.  Also a cheap ASUS/Nvidia V-9400X AGP video card.  It runs any Linux distro.  Oh, sure, not as fast as a modern PC, but I'm often surprised by how snappy it feels.  The key is stuffing as much RAM in as the mb will support.

If I was trying to get some mileage out of an old board like that, I'd giv it a tune-up.  Pull off the CPU heatsink, clean it and apply new paste, and replace the CMOS battery.

---

### Post by Arcturus691 on 2009-08-30
Just a shot in the dark.  You said the machine was really old and locking up.  The first thing I would do is make sure the machine is not overheating. Get a can of compressed air or an air compressor and dust it off.  By the way I have run ubuntu 8.10 on a dual PIII with 768mb of ram and it actually ran fairly good.

---

### Post by 3rdalbum on 2009-09-01
> **Arcturus691 said:**
> Just a shot in the dark.  You said the machine was really old and locking up.  The first thing I would do is make sure the machine is not overheating.

It's not locking up, it's waiting for the password to be typed.

---

