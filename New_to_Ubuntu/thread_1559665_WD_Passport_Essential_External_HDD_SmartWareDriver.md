---
title: "WD Passport Essential External HDD SmartWare/Driver Issues"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by nair on 2010-08-23
I've got a dual boot setup for work on my laptop made up of Windows Server 2008 R2 (x64) and Ubuntu 10.04 (x64).  I just recently got a _WD Passport Essential 750GB external harddrive_ to use with my laptop.  After first plugging it into my laptop for use on Windows, I noticed a bunch of so-called SmartWare that automatically creates a virtual drive on my machine, houses a bunch of other documentation, supposedly enables other software updates (to the external and/or internal drive?), and in general just takes up space (although not much).

I did not want any of this trash/malware, so I used the 'diskpart' command and other commands on Windows to repartition the entire drive as one single partition, thereby eliminating any hidden partitions which might house this SmartWare.  Then, I formatted the whole thing as NTFS.  Note that I am not sure if there was even a hidden partition to eliminate; I was simply hoping that this was the source of my problem that I could easily handle by reformatting.

After completing this process, I noticed that Windows could not see the external drive anymore.  So I rebooted, disconnected and reconnected the drive, tested a second USB cable, and still could not get it to recognize the drive.  I then booted into Linux and could see the drive.  And not only that, the SmartWare that used to simply appear on the desktop in Linux had disappeared.  So clearly, the 'diskpart' process I went through did something to erase or disable the SmartWare.

The problem I have now is that Windows will not recognize the external drive by simply connecting the drive via USB.  It used to automatically install drivers upon connecting.  Now, nothing happens, and I cannot even see the drive in the 'Computer' view or Device Manager.  After poking around on the Western Digital website, I think I might have to reinstall the SmartWare to get the drive functioning for Windows again (if that is even possible, since Windows cannot currently recognize the drive).  Unfortunately, this SmartWare seems to be some sort of coupling of both software and firmware, making it such that I can either have all of it or none of it.  I fear I am stuck with either a functioning drive that has additional Smart/MalWare lingering or with a drive that Windows will never recognize but is cleansed of all SmartWare.  Are these my only two options?  Have I potentially ruined this drive?  Is it even possible to get this drive back to its original state?

---

### Post by cjv8888 on 2010-08-23
Try re-formatting the drive in linux to NTFS again.
May be the partition table was corrupted at the first format under Windows.

---

### Post by inameiname on 2010-08-23
I second cjv8888's advice. Reformatting is the best option.

---

### Post by nair on 2010-08-24
Somebody at the office helped point me in the right direction.  All I needed to do in Windows was use the 'Disk Management' utility to assign it a drive letter (and I think also make the disk active; I can't remember whether I did or not using the command prompt in Windows).  I gave it a letter of E and now it is visible under 'Computer'.  I am curious though, is it also possible to assign this drive letter--using Linux--for the sake of Windows knowing what it is (ex. assigning as drive E and having Windows acknowledge it as drive E)?

I am assuming I could have done everything I did in Windows using Linux with a tool like GParted or via the Terminal.  I've never used GParted before.  Also, I never tried reformatting in NTFS using Linux, partially because it took me 7 hours to do in Windows and partially because I don't know how to do it.

Lastly, I have one additional follow-up question: Is there anyway I can confirm that I cleaned the drive of all SmartWare?  I am assuming that it is all gone because I have not found any yet...and it does not mount the virtual drive like it did before.  I have just heard rumors about some of this junk being embedded in firmware, which would be a problem I would not know how to address.  Hopefully, this drive will now function as I would expect any newly purchased external HDD: malware-free.

---

