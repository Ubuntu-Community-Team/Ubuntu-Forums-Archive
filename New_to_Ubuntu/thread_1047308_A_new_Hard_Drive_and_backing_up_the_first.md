---
title: "A new Hard Drive and backing up the first"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by iball8888 on 2009-01-22
OK i just got a new hard drive (this only a 120 and i got 350...money is tight :().  Is there a way i can backup everything?  Like all my software and settings and drivers, and etc  so that all i have to do after installing the new drive is just load it up and not have to do all that other stuff?

---

### Post by anewguy on 2009-01-22
Are you just Ubuntu, or are you dual boot with Windows?  If you are dual-boot with Windows, you can use Macrium Reflect that creates a file image of a partition or disk and then uses a rescue CD (either the one you build from the product itself or Bart with the product added to it) to restore that image to any other disk as long as it is big enough.

Also, if you have another port/cable to plug the drive in, there are Linux products that work like Ghost to copy your drive.  you can search these forums or search yahoo or google for ubuntu ghost utility.

Dave :)

---

### Post by MrKlean on 2009-01-22
You could also use remastersys which will make a live/install dvd of your system.. exactly as you have it now. And it's for Ubuntu AND it's free ; )

---

### Post by Insightfill on 2009-01-22
If it's a desktop PC, then the easiest route is to put the new drive in along with the old one (adjusting master/slave jumpers if necessary), boot the PC with an Ubuntu "Live CD", and use the Partition Editor program from the "System>Administration" menu.  Use this tool to copy the smaller partition to the larger one, resize the old partition to fill the whole drive, then make the partition bootable.

Then: power down the machine, take out the older drive, and power up with the new one in place (did you have to change master/slave if ATA?).  If everything looks good, then you might want to power things down and add the old drive back in, but use that same partition program to wipe it and put on a new, tidy EXT3 partition so you have a total of 470GB!

If it's not a desktop machine but a laptop, then you're going to need to find a way of doing the same steps, but to an outside source.  An external 2.5" drive enclosure is one option, and come as cheap as $10.  Put the new drive in the enclosure, back up everything to the USB drive using the steps above, then swap the drives.

A last option would be to use a CD such as CloneZilla (Debian-based) to back up your current machine.  This neat little utility can backup a drive from disk to another, or across a USB or network connection.  Pretty nifty.

---

### Post by Cracauer on 2009-01-22
> **iball8888 said:**
> OK i just got a new hard drive (this only a 120 and i got 350...money is tight :().  Is there a way i can backup everything?  Like all my software and settings and drivers, and etc  so that all i have to do after installing the new drive is just load it up and not have to do all that other stuff?

This is for the boot drive?

---

