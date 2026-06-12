---
title: "help me uninstall windows xp"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by austin7 on 2009-05-10
how do i uninstall windows xp im currently on dual boot with ubuntu 8.04 and i cant figure out how to uninstall windows

---

### Post by TheNosh on 2009-05-10
just delete the partition with windows on it using "Gnome Partition Editor" (gparted) from the repositories. if you have any important data on your windows partition be sure to back it up first.

---

### Post by austin7 on 2009-05-10
could u explain to me step by step how to do that sry i just got ubuntu today

---

### Post by TheNosh on 2009-05-10
first off, how did you install ubuntu? with Wubi, or on it's own partition with the installer CD?

---

### Post by austin7 on 2009-05-10
wubi

---

### Post by albinootje on 2009-05-10
> **austin7 said:**
> wubi

With Wubi you will need to keep your Windows installation as long as you use Wubi (inside Windows).
If you're happy with Wubi you can transform it into a real Linux partition, see here : [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by TheNosh on 2009-05-10
in that case, i think it's installed as part of your windows partition and unfortunately to uninstall windows would also get rid of your wubi ubuntu installation. so at that point the only way would be to make a fresh install of ubuntu from the installer CD
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

(that would get rid of all your files and settings so back up your data first)

maybe google around a bit to see if theres a way to expand a wubi installation to a full installation, but i'm pretty sure there isn't

before you do any of this, make sure you're ready to entirely get rid of windows

edit: only do this if you want a fresh install (which if you only got ubuntu today probably wouldn't really hurt)

---

### Post by TheNosh on 2009-05-10
> **albinootje said:**
> With Wubi you will need to keep your Windows installation as long as you use Wubi (inside Windows).
If you're happy with Wubi you can transform it into a real Linux partition, see here : [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

well in that case, disregard what i said, it appears you're in luck and can keep your settings and such. (this is why i encourage googling first)

---

### Post by Ravernomina on 2009-05-10
to make it simple.... just back up uyour files then download ubuntu ISO burn it to disk. Then restart after that go to you boot menu in BIOS. insert you CD then go down to CD-rom boot. Boot up with "test ubuntu without changes to your computer" then after that got to system>admin>partition editor. open it up look for a partiton that has A NTFS file system delete it if u backed up your data. then start the install of ubuntu.

Link for ubuntu ISO: [www.ubuntu.com]("www.ubuntu.com")

---

### Post by austin7 on 2009-05-10
i dont think its in windows anymore because when i start up my computer it gives me a choice to choose windows or ubuntu

---

### Post by TheNosh on 2009-05-10
> **austin7 said:**
> i dont think its in windows anymore because when i start up my computer it gives me a choice to choose windows or ubuntu

thats what wubi does

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by Ravernomina on 2009-05-10
thats a boot loader so its still windows :P a boot loader just tells the computer ware to boot from :P well it tells the BIOS ware

---

### Post by austin7 on 2009-05-10
soo what should i do

---

### Post by austin7 on 2009-05-10
???

---

### Post by GMachine_24 on 2009-05-10
Hi Austin:

It seems you want to remove Windows, but it also seems you will need to reinstall Ubuntu after you do because you used Wubi to install Ubuntu. Esentially you  will be installing Ubuntu to a blank hard drive - i.e. from scratch. If you're willing to do that - i.e. erase your hard drive (including Windows, Ubuntu and all data) - let us know and we can help you proceed.

Please be sure to specifically answer these questions - no one here wants to help you wipe a hard drive if that's not what you want.

--GM

---

### Post by austin7 on 2009-05-10
yessir that is what i want to do ive got my files that i need on an external drive

---

### Post by TheNosh on 2009-05-10
if you just got ubuntu today, i would honestly advise that you keep your windows installation a while longer untill your positive you're ready for the switch

if you're sure you wanna do it now though, i can't really stop you. just back up your important data and run the installer CD at startup. it will automatically install over windows by default.

[http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn) <-- here's how to burn the CD if you need any help with that

---

### Post by austin7 on 2009-05-10
i dunno how to run the cd at startup thats the problem

---

### Post by TheNosh on 2009-05-10
> **austin7 said:**
> i dunno how to run the cd at startup thats the problem

you just need to have the CD in when you start the computer, most systems have CD first on the boot list so it does it automatically but if yours doesn't you can go into the BIOS and change the boot settings, or when you start up try going to boot options and selecting CD

---

### Post by austin7 on 2009-05-10
mmk umm im downloading ubuntu-9.04-desktop-i386.iso in my ubuntu os i then burn it to a disk and leave the disk in and restart my computer

---

### Post by TheNosh on 2009-05-10
> **austin7 said:**
> mmk umm im downloading ubuntu-9.04-desktop-i386.iso in my ubuntu os i then burn it to a disk and leave the disk in and restart my computer

yes, that should be it

---

### Post by austin7 on 2009-05-10
hey thanks alot i really appreciate the help im sry i was so slow

---

### Post by GMachine_24 on 2009-05-10
Austin:

You needn't apologize. We were all beginners at some point.

If you run into a problem installing Ubuntu on a hard drive that had/has Windows - there is an easy fix for that. It might happen - it might not. It has happened to me and some other Ubuntu users. If it happens just post a note here and I (or someone else) can walk you through what you need to do. Hopefully, it won't be necessary.

Good luck and I hope you enjoy Linux/Ubuntu.

--GM

---

### Post by TheNosh on 2009-05-10
no problem

good luck and be sure to come back if you need any more help, it's kinda what we're here for :wink:

---

