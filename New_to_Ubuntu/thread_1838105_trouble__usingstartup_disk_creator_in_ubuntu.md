---
title: "trouble  usingstartup disk creator in ubuntu"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by evaramos on 2011-09-03
hi i been trying to format my  usb in disk creator but it doesn't let me a box appear saying cant mount the usb it cannot find the private volume monitor i don't understand  why it say that. this is for my big computer by the way

also in my netbook i been trying to bootup  to install 10.04ubuntu but is said it cannot do it because there's a unknown file when i use the disk creator it doesn't have the format part so i just click make startup disk and is installed perfectly in the usb but when i open the usb one of the file has a lock on it so i wondering if that the problem

thank you

---

### Post by walt.smith1960 on 2011-09-03
I've had better luck using Unetbootin than I've had with startup disk creator.  Unetbootin can be found via Synaptic or the Software Center.

---

### Post by Isaacgallegos on 2011-09-04
It sounds like you have two different problems for two different systems. Maybe just pick system for now for us to work with? 

Can you list out exactly what steps you're doing and what the computer's doing, so we can have a better idea of what's happening? 

THANKS! :KS

---

### Post by evaramos on 2011-09-04
here is the steps i did using the disk creator

i download ubuntu version 10.04os(LTS) in my computer

next i   open the startup disk creator to setup my usb 

when i click the makeup disk the  version ubuntu 10.04LTS was installed  in the usb i didn't have any problem it was simple 
it was ready to boot it.

when it was time to boot it in the computer it appear in the screen  saying that there was an unknown file in the version ubuntu 10.04os and it couldn't continue with the booting?

what might be the problem?

also i did open the installed files in the usb too se if there was a problem.  and it appears one of the file has a lock on it, the file name is ldlinux.sys and this file contain a lock within it.

one more thing in my startup disk creator it doesn't have to format the usb it only appear erase disk instead of format,

 my  other question is not formatting the usb  be another problem  for not be able to installed ubuntu correctly?

thank you

---

### Post by Isaacgallegos on 2011-09-04
Quick question. What computer is this on? :confused: 

> **evaramos said:**
> 
when it was time to boot it in the computer it appear in the screen  saying that there was an unknown file in the version ubuntu 10.04os and it couldn't continue with the booting?



Can you write out the exact error message? This could help. I'm wondering if it's just your mother board saying "remove usb to continue booting". That's a common error, not related to ubuntu. However, I can't be sure unless you post the exact error.

 Thanks. 



> **evaramos said:**
> 
also i did open the installed files in the usb too se if there was a problem.  and it appears one of the file has a lock on it, the file name is ldlinux.sys and this file contain a lock within it.

Don't try to edit the installer, unless you're veerry good at programming. :lolflag:

---

### Post by westie457 on 2011-09-04
> **evaramos said:**
> here is the steps i did using the disk creator

i download ubuntu version 10.04os(LTS) in my computer

next i   open the startup disk creator to setup my usb 

when i click the makeup disk the  version ubuntu 10.04LTS was installed  in the usb i didn't have any problem it was simple 
it was ready to boot it.

when it was time to boot it in the computer it appear in the screen  saying that there was an unknown file in the version ubuntu 10.04os and it couldn't continue with the booting?

what might be the problem?

also i did open the installed files in the usb too se if there was a problem.  and it appears one of the file has a lock on it, the file name is ldlinux.sys and this file contain a lock within it.

one more thing in my startup disk creator it doesn't have to format the usb it only appear erase disk instead of format,

 my  other question is not formatting the usb  be another problem  for not be able to installed ubuntu correctly?

thank you

Hi, suggest you try again.
The only thing you need to change in the routine you have been using is to erase the usb stick.

This actually formats the stick creating a bootable partition and a partition for the .iso file as fat32 so it can be read by any computer.

Creating a persistence file for saving things to is an option you may or may not want to use

---

### Post by evaramos on 2011-09-04
this is what it said in the screen
ERROR: NoConfiguration filefound
No Default or UI Configuration direactive found.

---

### Post by Isaacgallegos on 2011-09-04
> **evaramos said:**
> this is what it said in the screen
ERROR: NoConfiguration filefound
No Default or UI Configuration direactive found.

After reading around I found that this is related to the grub not recognizing the iso, or the usb is making the grub (the thing that makes the usb bootable) with out including the Ubuntu install files. 

2 possible solutions:

1. Try reformatting that usb drive. 
2. Find a different method to load the iso to the usb (I doubt you have to do this...) 

To really reformat that drive, insert the usb and open your "Disk Utility". Found in System>Administration>Disk Utility
Picture:

[[IMG]http://img685.imageshack.us/img685/7829/screenshotya.png[/IMG]](http://imageshack.us/photo/my-images/685/screenshotya.png/)


Now, select your USB drive!!! Not anything else! Then unmount is volume, otherwise it wont let you format.
Picture of me doing it:


[[IMG]http://img577.imageshack.us/img577/2535/screenshotsm.png[/IMG]](http://imageshack.us/photo/my-images/577/screenshotsm.png/)

After that, click on format volume. See picture below:

[[IMG]http://img15.imageshack.us/img15/6929/screenshot1qk.png[/IMG]](http://imageshack.us/photo/my-images/15/screenshot1qk.png/)


A new window will open. Click on its drop down menu and select "FAT". 

[[IMG]http://img705.imageshack.us/img705/1614/screenshot2yo.png[/IMG]](http://imageshack.us/photo/my-images/705/screenshot2yo.png/)

Now press format: 

[[IMG]http://img594.imageshack.us/img594/962/screenshot3rb.png[/IMG]](http://imageshack.us/photo/my-images/594/screenshot3rb.png/)

There are other ways to do this. I think you would like the more graphical approach.

---

