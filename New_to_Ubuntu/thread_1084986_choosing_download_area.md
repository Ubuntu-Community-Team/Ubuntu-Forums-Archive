---
title: "choosing download area"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by eurythmic on 2009-03-02
a friend cut a cd for me (ubuntu) and there is an error reading the disk on installation. When i boot from the disk it works enough to go on the net. When i download it says i don't have enough space, and tells me to choose another location. During download i am never given the choice of where to download. How can i choose the location of where to download, and why do i run out of space when i have a nearly empty 10 gig drive?:mad:

---

### Post by taurus on 2009-03-02
Have you installed Ubuntu on your harddrive or are you still running it from the CD--LiveCD session?

---

### Post by wilbbe01 on 2009-03-02
You are booted off of the disk, you don't have your drive mounted more than likely.  The simplest way is to click on places, choose Computer, then double click your drive.  Then when saving a link in firefox you can right click and choose save as or whatever.  I think that will do it, but if it doesn't you can always go to the edit menu in firefox and choose preferences.  After that you can choose "ask me" in the download files section.  Choose your hard drive.  Of course your drive has to be formated first if it isn't right now.

---

### Post by eurythmic on 2009-03-02
cheers ben and taurus. Does my drive have to be re-formatted? I am still running off the cd but i tried to in stall and it gets to 75mb and says out of space, but i can see my 10gig hard drive on my desktop, it seems to be recognised and formatted. I'll try all your suggestions, thanks, i may be back. Andy

---

### Post by taurus on 2009-03-02
Open a terminal from the LiveCD and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

---

### Post by egalvan on 2009-03-02
Do you want an Ubuntu-only install?
This will be fairly easy.

Do you want to share (dual-boot) with Windows XP?
This is slightly more work to prepare.

Either way, be sure to give the info asked by the others.

sudo fdisk -l

---

