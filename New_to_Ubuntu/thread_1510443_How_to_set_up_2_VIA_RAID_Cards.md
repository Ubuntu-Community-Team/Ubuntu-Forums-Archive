---
title: "How to set up 2 VIA RAID Cards?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Beeker_410 on 2010-06-15
Hello there! Right now, I am a very confused newb about this ... I have 2 VIA Raid cards in my system (VT6410) running Ubuntu 10.04. Disk Utility DOES see them using the pata_via driver but the hard drives attached to them aren't showing up. How do I set the cards up so that the drives are seen? I really don't want an actual RAID, I just want the JBOD setting. All the drives are ATA drives (not SATA) with new cables if that helps. I have the ad.4, ataraid.4, and ar.4 files. Where do I put these files? 

I've tried basically everything I can think of to get these things to work including switching around jumpers, running some RAID discovery tools all to no avail. I need some serious hand holding at this point please or at least pointed to a really good tutorial that I can follow.

Plz halp! Thanks :)

---

### Post by psusi on 2010-06-15
What does sudo dmraid -nv show?

---

### Post by Beeker_410 on 2010-06-15
It says that there are no RAID disks but there are disks attached :confused:

---

### Post by Beeker_410 on 2010-06-15
I just ran sudo varmon and it says DAC driver not loaded. Where do I get this driver?

---

### Post by psusi on 2010-06-15
I have no idea what varmon is, but the only driver you should need is the via one.  What does ls /dev/sd* show?  And sudo blkid.

---

### Post by Beeker_410 on 2010-06-15
/dev/sda, sda1 (UUID="XXXXXXXX..." type="ext3") , sda2, sda5 (UUID="XXXXXXXX..." type="swap") then sdb1 sdb5 sdb6 sdb7 sdb8 sdb9 (Type="ufs"). 

EDIT:
Never mind about the sg0 sg1 sg2 :/

---

### Post by psusi on 2010-06-15
Ok, looks like you have two drives.  How many do you have plugged in?

---

### Post by Beeker_410 on 2010-06-15
I have 5 more drives. Four plugged into 1 card and 1 drive plugged into another. All set to Cable Select. I did try setting the Master / Slave thing on each and no luck there either. 

How do I set the BIOS on the cards to recognize these drives? Can I use a thumb drive or something? Oh and how do the ad.4, ataraid.4, and ar.4 files figure into all of this?

---

### Post by Beeker_410 on 2010-06-16
Okay. Good news is that after I reinstalled 8.10 (fully intending to upgrade through Update manager ) I CAN see a few more disks. The bad news is that now my onboard ethernet port is not responding grrrrrrrrrrrrrrr :(

---

### Post by Beeker_410 on 2010-06-16
I got the driver, and so long story short at least one of the VIA cards seem to be working now. All I had to do apparently was just reinstall the OS. Now onto getting the drives to actually mount ...

---

### Post by Beeker_410 on 2010-06-18
I give up, can somebody plz tell me how I can get this to work correctly? I did check this site out but I'm a bit unsure how to proceed: [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) Will any of it work / help?

---

