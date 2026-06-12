---
title: "Update seemed to crash, now cannot reinstall!"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Grimeandreason on 2010-10-01
Hi guys, absolute newbie here so I'll explain my problem...

When I tried to update my ubuntu, it wouldn't boot up afterwards.  It said something had failed, or was missing, and led me to a DOS type screen with which I personally could do nothing!!

I got an ubuntu CD and tried to reload it.  It got through to the partition screen but nothing showed and all the choices were blank.  I could not progress.

I tried rebooting without the CD in and, after prompting, put the CD back and loaded ubuntu off the CD.  I now have the desktop, but when I try to install from there, exactly the same thing happens.

I think my hard-drive might be screwed, but the fact that my computer failed so soon after the update (possibly the first reboot if I remember rightly) i'm loathed to get a new hard-drive until im sure it isn't a software issue.

If i go to disk utility, the 'floppy drive' shows No Media Detected and the only other things down the right hand column are CD/DVD and the Ubuntu CD ISO.  How can I tell for sure if my hard drive is ****ed?  Should my hard drive appear on this screen?

Please, if replies could be kept as jargon free as possible I'd be most grateful!

Ben

---

### Post by Hippytaff on 2010-10-01
There could be a number of reasons why this is happening. Did you burn the disc?

---

### Post by Grimeandreason on 2010-10-01
No, the disk is an offical ubuntu one that they sent to my dad.

---

### Post by Hippytaff on 2010-10-01
Do other discs work in the hard drive?
 
If your running windows yYou could try a wubi install for the time being, until you diagnose the issue!?
 
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by plucky on 2010-10-01
From the Live Cd open a terminal and ```
sudo fdisk -l
``` to see if the hard drive is still there.
If it is, run **Gparted** and see what that finds in the way of partitions.

If it does find partitions,there is an option in Gparted to run a check on the partitions.Do so.

If it isn't there,enter setup in the BIOS and see if the BIOS can see the hard drive.If it can't then you have a bad drive.

Reseat the connections to the drive and see if it now works.


Good Luck

---

### Post by Grimeandreason on 2010-10-01
Thanks for the replies.  Im off out now but I shall check whats been said so far when I get home in a couple of days.  I think I went into Gparted and I don't think it showed anywhere.  I wasn't on XP or windows, though I had a copy of vista in the virtual box (had been running on Ubuntu previously.

How do tell if BIOS can recognise my hard drive?  Is it to do with the IDE Channel malarky?  

It says:                 channel 0 master [Optiarc DVD RW AD-72] 
                            channel 0 slave    [none]
                            channel 2 master [none]
                            channel 2 slave    [none]

                            drive A                [1.44M, 3.5"]
            
At bottom it says:  Base Memory        640k
                            Extended Memory 959M

Nowhere can I see the words 'Hard drive'.  Why can't it be simple lol!?

---

### Post by Grimeandreason on 2010-10-01
Oh, and if I try to let it boot up without the CD in, it gets to 'verifying DMI pool data.......'

Then I get this message:

Boot from CD/DVD:
DISK BOOT FALIURE, INSERT SYSTEM DISK AND PRESS ENTER.

---

### Post by Grimeandreason on 2010-10-01
Is there any way, from what I can access, of wiping the hard-drive and starting again?

---

### Post by plucky on 2010-10-01
> **Grimeandreason said:**
> Is there any way, from what I can access, of wiping the hard-drive and starting again?

If the Bios cannot see the drive,you have no way of doing anything with the drive.Check the connections and if that doesn't work,it will probably need replacing.

Good Luck

---

### Post by QIII on 2010-10-01
Is it a Seagate drive with the SD15 firmware?  If it is, you may be able to salvage the drive and get it running again without loss of data.

The firmware should be printed on the paper label.

---

### Post by Grimeandreason on 2010-10-01
mmm I have no idea QIII, its been a couple of years since I put it together.  I'll check the connections when I get home and if not I guess it's a new hard drive for me!

Plucky, if the BIOS could see the hard drive, what should I see?

---

### Post by plucky on 2010-10-01
> **Grimeandreason said:**
> mmm I have no idea QIII, its been a couple of years since I put it together.  I'll check the connections when I get home and if not I guess it's a new hard drive for me!

Plucky, if the BIOS could see the hard drive, what should I see?

It depends on the Bios,but most will tell you the size of the disk and the maker if the disk.

From your previous post >  How do tell if BIOS can recognise my hard drive? Is it to do with the IDE Channel malarky?

It says: channel 0 master [Optiarc DVD RW AD-72]
channel 0 slave [none]
channel 2 master [none]
channel 2 slave [none]

drive A [1.44M, 3.5"]

It shows the DVD but no HDD.

Good Luck

---

### Post by QIII on 2010-10-01
Before you buy a new hard drive, let me know if it is a Seagate with the SD15 firmware.  I can point you in the direction of a possible solution.  I've used the method several times to get bricked Seagates running again.

(Eh.  It takes a week or so to get some parts ordered and a trip to your local electronics store for some terminals, so it's not an immediate fix.  Maybe the new drive is in order and you can get the other running to get your important data off of it.)

---

### Post by Grimeandreason on 2010-10-07
Thanks for the help.  It's not a seagate unfortunately.  Once I had taken it out I could hear a slight rattle if I shook it.  Not Good.  I managed to get my hands on an HP Compaq which I took the 40G hard Drive out of in an attempt to replace my hard drive, but when I got down to it I found it had different connection ports.  Mine had very slim ports but the HP has check pin type ports.  I'm thinking I might just have to use the HP until I can buy a new hard drive?

---

### Post by QIII on 2010-10-08
To get your data off, you might try the "refrigerator" method.

Put the drive in a fridge until is is good and cool.  Try running it just long enough to get data off of it.

The problem is that the rattling is probably the heads bouncing off the platters and doing damage.  If the platters are damaged, the likelihood of salvaging your data is very small.

---

### Post by Grimeandreason on 2010-10-09
Thanks for the help QIII.  It's OK though, everything I had that was important was backed up online.  I'm just gonna use this HP until I get a job and can afford a new hard drive!

I was using Ubuntu coz microsoft recognised my cracked copy.  Now I have a genuine XP, should I stick with it or go for the latest Ubunt... I can't decide!

---

