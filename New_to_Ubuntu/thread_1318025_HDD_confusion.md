---
title: "HDD confusion"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by mcclunyboy on 2009-11-07
Hi,

My hard disk is dying.

I have a new much bigger one to replace it.

How do i install Ubuntu on it.

I plugged them both in and booted it up, then put the Ubuntu disk in, rebooted, booted from disk and installed Ubuntu on the new 500GB disk as the entire partition...i expected this to work - why wont it?

What can i do to get it to work?

---

### Post by ivanvajar on 2009-11-07
Make sure your new HDD is bootable in BIOS or unplug your old HDD, replace it with new one and install Ubuntu.

---

### Post by mcclunyboy on 2009-11-07
i trie just swapping them over but the new one didnt boot ...

how do i make it bootable - when i installed it and selected new HDD it just says grub - failed to boot or something similar.

---

### Post by Bartender on 2009-11-07
Are the drives PATA or SATA?

---

### Post by mcclunyboy on 2009-11-07
pata these 1s

---

### Post by Shazaam on 2009-11-07
Simple fix (as long as you didn't wipe the old drive)...
1. Download and burn a Clonezilla (or similar) livecd (or you can use the dd command).
2. Set drive jumpers- Primary for old, Slave for new.
2. Wipe NEW hard drive clean.
3. Set your pc bios to boot from cdrom first in the boot order.
4. Boot cloneing app cd and clone old drive to new drive (direct disk to disk).
5. Remove old drive and change jumpers on the new one to Primary.
6. Enjoy
You may later want to add/resize partition(s).

3 tools you need...
A. GParted livecd-
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
B. Clonezilla-
[http://clonezilla.org/](http://clonezilla.org/)
[http://clonezilla.org/clonezilla-live/doc/](http://clonezilla.org/clonezilla-live/doc/)
C. SuperGrubDisk (not as important but good to have)-
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://members.iinet.net.au/~herman546/p15.html#Common_Booting_Errors_and_Some_Possible](http://members.iinet.net.au/~herman546/p15.html#Common_Booting_Errors_and_Some_Possible)

I cloned a dying drive (click of death, locking up, wouldn't boot) to a new drive with zero errors

---

### Post by mcclunyboy on 2009-11-07
i was just looking up these jumpers...what are they - from the 3 connections on each hard disk i only have the power/data cable..

i always thuoght master/slve depended on which connection u attached t5o (end one = master and middle = slave)

---

### Post by cascade9 on 2009-11-07
Depends. If your drive is set to 'cable select' thats what happens, but if the drive is set to master, or slave, that overrides the cable selection. Most of the time there is just the 3 settings- master, slave, cable, eg-

[http://members.cox.net/yesshows/CD6.jpg](http://members.cox.net/yesshows/CD6.jpg)

Sometimes there are extra unused jumpers- 

[http://img.tomshardware.com/de/2005/11/16/das_grosse_thg_stecker_kompendium/hdd_jumper_ma.jpg](http://img.tomshardware.com/de/2005/11/16/das_grosse_thg_stecker_kompendium/hdd_jumper_ma.jpg)

Very rarely, you will get odd settings-

[http://studynotes.net/images/seagate-jumpers.gif](http://studynotes.net/images/seagate-jumpers.gif)

---

### Post by mcclunyboy on 2009-11-08
hi both HD's are Western Digital but the new one is picked up in Bios but it wont boot.

Is there a reason this doesnt work:

 - have new drive as slave and old as master
 - install ubuntu onto New drive including GRUB(under advanced settings within install)
 - take old once installation is finished
 - when it boots up it freezes on the bootup screen...trying to find device or primary master or soemthing.

---

### Post by cascade9 on 2009-11-08
Sounds like its trying to boot from master. Shazaams post makes me think that you will need to remove the old drive, change the new drive from 'slave' to 'master' and then it should work.

---

### Post by Bartender on 2009-11-08
Unless you're an incredibly lucky person, you will not make progress on this until you have a firm grasp on the master/slave jumpers and cable position dynamics.

If both drives are set to cable select AND you have an 80-wire PATA cable, then you can plug the two drives onto either of the two clips on the ribbon cable, then go into BIOS and tell BIOS which HDD to boot first.

If you do _not_ have an 80-wire cable, then you need to know without a doubt how to set each HDD's jumper in order to choose "master" and "slave".

You also need to know which clip on the ribbon cable is the "primary" clip.  If I recall correctly, the last clip is the primary position.  The one in the middle is secondary.  If you jumper your HDD as "master", then connect it to the secondary clip position, it will probably not work.  

Strip both HDD's off the cable.  Set aside the old HDD.  Jumper your new HDD as "master" and connect it to the primary clip.  Boot the PC.  Go into BIOS.  The HDD should be recognized, and you should be able to set it as bootable.  If you can't, shut down the PC, move the HDD to the secondary clip (the one in the middle of the ribbon cable), and try again.  If you cannot set the new HDD as bootable on either clip, and you're POSITIVE the jumper is set to master, then you have a hardware problem.  The ribbon cable is broken, or the HDD has a bent pin, or it's broken (not the first time that's happened), the motherboard is OOS, the power supply isn't providing enough power to the new HDD, etc.

If you're having problems with the new HDD, go thru the above process with your original HDD.  By the time you're done you'll have a better understanding of the jumper/clip position questions.  

Since the PC was working before, chances are it's the ribbon cable or the new HDD if you do have a hardware problem.

EDIT:  I forgot about the "single" jumper setting.  When doing the above exercise, you should probably try jumpering the HDD to the "single" setting instead of "master".  That's when you're experimenting with only one HDD.  As soon as you try connecting BOTH drives, be sure to use "master" on one and "slave" on the other.  I'm not sure about this, but I think I've connected a single HDD successfully when jumpered as "master" or "single".  Maybe not :)

---

### Post by Shazaam on 2009-11-08
Gotta love bartenders. Sage advice!  :)

"I'm not sure about this, but I think I've connected a single HDD successfully when jumpered as "master" or "single". Maybe not" 
Yes, it will work like that.

---

### Post by mcclunyboy on 2009-11-09
I dont have any jumper cables.  The pata cables available are for data/power only.

I tried connecting the new one to Primary and the old to secondary and i didnt have any success.

The bios is not useful, it literally only offers you a boot order without any other options - unless I am pressing the wrong Fkey - I press all of em because I couldn't find the right one.

I will see if i can find the jumper cables for master/slave but I didnt see any.  I have it installed/working on the old hard disk just now ( its tempermental though, sometimes doesn't boot but most of the time it does - i will run that fchsk or whatever it is tonight to see if the hard disk is in a bad state or not.

---

### Post by mikechant on 2009-11-10
The PATA discs I've used didn't have jumper **cables** - they had a set of jumper pins next to the power/data connection and you used a tiny 'bridge' to connect a pair of pins together.

Here's a photo:

[http://www.cromwell-intl.com/technical/ata-ide-sata-usb-cable-pinouts.html](http://www.cromwell-intl.com/technical/ata-ide-sata-usb-cable-pinouts.html)

The second picture down shows the back of a PATA drive, with the data connection left, power right, and jumpers in the middle. If you look carefully you can see that the two left most jumper pins are connected with a grey bridge.
I've got a feeling that the jumper postitions vary by drive model/make but they may have some indicator letters next to them or you may be able to find a manual (with jumper settings) for your particular drive online.

---

