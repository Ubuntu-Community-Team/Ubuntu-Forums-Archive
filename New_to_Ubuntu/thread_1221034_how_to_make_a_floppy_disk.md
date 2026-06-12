---
title: "how to make a floppy disk"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-07-23
I've never used the floppy drive on any computer I've owned, but in my little project to convert an old windows 98 box to puppy linux I found it has no option to boot from a cd. Will I need any particular app to save an iso to a floppy disk in my Ubuntu box?

thanks 
myst

---

### Post by ymra on 2009-07-23
I have never used it so I cant tell you how to use it.  The command dd is used to copy disk images to a floppy disk. If you want to use windows find a program called rawwrite.

---

### Post by LewRockwell on 2009-07-23
> **mystmaiden said:**
> I've never used the floppy drive on any computer I've owned, but in my little project to convert an old windows 98 box to puppy linux I found it has no option to boot from a cd. Will I need any particular app to save an iso to a floppy disk in my Ubuntu box?

thanks 
myst

sidenote:

you may have the opportunity to upgrade the BIOS to a newer version which may then boot from CD

.

---

### Post by mystmaiden on 2009-07-23
thanks ymra. No, I'm not wanting to use windows. 

Surely there is more to the command to make a bootable floppy than just dd? I'm really new to the terminal still.

myst

---

### Post by mystmaiden on 2009-07-23
Lew wrote: 


you may have the opportunity to upgrade the BIOS to a newer version which may then boot from CD


That'd  probably be a better solution altogether. How would I go about finding out if there is an upgrade available? I haven't a clue. 

myst

---

### Post by LewRockwell on 2009-07-23
these should help you:

[http://www.puppylinux.com/hard-puppy.htm](http://www.puppylinux.com/hard-puppy.htm)

[http://www.murga-linux.com/puppy/viewtopic.php?t=7979](http://www.murga-linux.com/puppy/viewtopic.php?t=7979)

[http://answers.yahoo.com/question/index?qid=20070902003806AALb4XQ](http://answers.yahoo.com/question/index?qid=20070902003806AALb4XQ)

.

---

### Post by LewRockwell on 2009-07-23
> **mystmaiden said:**
> Lew wrote: 


you may have the opportunity to upgrade the BIOS to a newer version which may then boot from CD


That'd  probably be a better solution altogether. How would I go about finding out if there is an upgrade available? I haven't a clue. 

myst

initiate a search using terms like bios update and the information from your equipment like make, model, part number, build number

if it's a custom computer you'll need to use the make and model of the motherboard

to see which version of BIOS you currently have...sometimes it shows on the start-up screen long enough to see it/write it down/etc

other times you'll need to go to the BIOS area during start-up(usually the "F2" key depressed about twice per second right after turning the power on...sometimes it's the "delete" key and on some really old machines it was a combination of keys like "control-alt-delete")

try F2 first

.

---

### Post by plucky on 2009-07-23
Try this link [Smart Boot Manager](https://help.ubuntu.com/community/SmartBootManager) to create a floppy that will boot a CD.


Good Luck

---

