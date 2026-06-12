---
title: "HELP!! Install Windows 7 from Ubuntu No DVD/USB"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by shawnnkushh on 2011-07-23
Ok i really need some help here.
I have a new HP laptop running 11.04 that I'm trying to install a clean Windows 7 Ultimate on, not a problem normally right.
 
My issue is, most new laptops don't have disc drives anymore, and I dont own an external disc drive either, so the DVD seems out of the question, I dont have a large enough USB drive to install that way, and im not quite sure if you can perform a PXE install over wifi, and im utterly confused how to install from iso in linux, and ive read wine is only a temporary enviroment, so im basically stuck for now. I've been researching this for 2 weeks now, and I'm still hopelessly lost. most of this linux stuff is still way over my head, and im just trying to get back to my comfort zone, windows.
 
if anyone could shoot me some easy ideas, or confirm if PXE is possible over wifi, all help would be greatly apreciated
I'll be checking back every few hours for replies thanks!

---

### Post by wildmanne39 on 2011-07-23
Hi, if you have the windows disk like you mentioned then you can install virtualbox and install windows in it. 

Here is a link read up on the documentation before you install virtualbox.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

This the only way I know of for you to use windows if you can not install with a dvd or usb.

---

### Post by shawnnkushh on 2011-07-23
so basically there is no way to load up the iso to begin the installation from memory? i dont really have ascess to a 4gig usb stick

---

### Post by wildmanne39 on 2011-07-23
Hi, no you can not do it from with in ubuntu unless you use virtualbox.

---

### Post by scradock on 2011-07-23
> **wildmanne39 said:**
> Hi, no you can not do it from with in ubuntu unless you use virtualbox.
Sorry, that is NOT true. You can use an .iso file on your hard drive as the boot "medium"; the issue is going to be getting it off the Windows install disc into the machine in the first place. For that, you will need to network two machines, one of which does have a CD/DVD drive, and copy the entire disc to the HD.

---

### Post by shawnnkushh on 2011-07-24
if this is indeed true, i already have the iso, on the HD how do i proceed from here?

---

### Post by shawnnkushh on 2011-07-24
also would i be able to install to hard disk from within the virtualbox?

---

### Post by wildmanne39 on 2011-07-24
Hi, windows would be on a virtual partition and not a physical partition.
 
You would be able to run ubuntu and windows at the same from within ububntu. Look at the link I gave you in my previous post it explains the whole thing.

---

### Post by subhagato on 2011-10-20
Follow the link

[http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc]("http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc")

---

