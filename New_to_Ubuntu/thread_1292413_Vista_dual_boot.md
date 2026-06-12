---
title: "Vista dual boot?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Bondy on 2009-10-15
Probably just a coincidence but evrtime I have tried to install Linux with a dual boot with vista it never goes straight forward first time

Could this just be a bug in vista all though I cant see that being a problem with installing booting maybe. So Im thinking it may be hardware issues thats certainly what it looks like when doing text insttals most of the errors seem to be acpi related to sound or graphics cards and dual cores the last I dont know why? how long have servers been dual core ffs. 

And the only reason I can see it being a hardware issue is because machines with vista pre installed are going to be relatively new

Surely bill couldnt be that sneaky

---

### Post by CRAY-4 on 2009-10-15
try installing from live cd

---

### Post by Jean-Danjou on 2009-10-15
Use "gparted Live CD" first, and make a NTFS partition the size u like for Vista. Reboot with Vista disk, Install. Then Ubuntu or what ever flavour u like. Bob's ur uncle!
Work for me this way. May the Force be with you!
Merci.

---

### Post by mapes12 on 2009-10-16
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by yanceypd on 2009-10-16
You will probably have better results if you defrag Vista maybe a couple of times then install Ubuntu from a live CD as previously sugested.  Then if you like to tinker I suggest Clonezilla to have things backed up.  Saves hours of reinstallation and updating.:)

---

### Post by tarps87 on 2009-10-16
One thing to check is that you shutdown vista, not hybernate it. It does strange things.
What are you using to install ubuntu (wibi, live cd, alternative cd, usb, mind control)

---

### Post by The Judderman on 2009-10-16
The main issue as has been hinted at is that Vista doesn't particularly like being resized. So if you use Gparted to manually resize the windoze partition, then you will have problems, and need to reinstall vista.

The solution to this is to defrag a couple of times, as mentioned, and then resize the partition in vista. (to do this, type partition resizing in the help menu in vista, and it will come up with the info to access computer management and what to do). Frustratingly, this doesn't always give you as much space as you would expect given the disk usage, but it will give you plenty to install ubuntu.

Once its been resized, boot up the live CD and install Ubuntu and enjoy!!!

What other problems do you get when you try to dual boot?

Hope this is helpful,

The Judderman

---

### Post by Bondy on 2009-10-19
yeah seems defraging did the the trick.

In future I think I will back up all the personal files and reinstall vista with a custom partion and then install ubuntu would be alot quicker

---

### Post by cptr13 on 2009-10-19
I never understand why people don't preach WUBI for completely new folks...
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.
It instals INSIDE windows, does no permanent changes to the hard drive and can easily be removed through add/remove software same as most Windows software.  It is PERFECT for new folks.  However, I strongly recommend a true install if you find you like Ubuntu :)

[https://wiki.ubuntu.com/WubiGuide#](https://wiki.ubuntu.com/WubiGuide#)

---

### Post by pgar23 on 2009-10-19
please mark as SOLVED.

---

### Post by tarps87 on 2009-10-20
> **cptr13 said:**
> I never understand why people don't preach WUBI for completely new folks...
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.
It instals INSIDE windows, does no permanent changes to the hard drive and can easily be removed through add/remove software same as most Windows software.  It is PERFECT for new folks.  However, I strongly recommend a true install if you find you like Ubuntu :)

[https://wiki.ubuntu.com/WubiGuide#](https://wiki.ubuntu.com/WubiGuide#)

It is probably because WUBI is not a 'true' version of Ubuntu, it is not running in a native environment e.g. the wrong file system and this can cause problem in itself. I would by no means call it perfect.

---

