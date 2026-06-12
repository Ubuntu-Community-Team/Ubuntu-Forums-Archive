---
title: "Setting up udisks froze PC while upgrading"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by DayLite on 2011-04-29
Upgrading to 11.04 froze at Setting up udisks (1.0.2-4ubuntul) How do I get around this without losing data and settings.

Only 3 minutes were left! Computer now frozen over for 30 minutes. . I have a desktop Compaq Presario SR1130NX

HELP !

---

### Post by DayLite on 2011-04-29
I had to shut down my computer. The grub allows me to start Windows XP but when I click on the Linux recovery mode nothing happens, tried all the other choices, no response :(

Gnu Grub version 

Ubuntu, with Linux 2.6.38-8-generic
Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
Previous Linux versions
Memory Test (memtest 86+)
Memory Test (memtest 86+, serial console 115200)
Windows NT/2000/XP (on /dev/sda1)
Microsoft Widows XP Home Edition (on /dev/dev/sda2)

tried all, only boots to Windows XP

---

### Post by fabricator4 on 2011-04-29
> **DayLite said:**
> I had to shut down my computer. The grub allows me to start Windows XP but when I click on the Linux recovery mode nothing happens, tried all the other choices, no response :(

Download the LiveCD and do a clean install from that.  If /home is the same partition as / you'll have to restore all your data from backups.  (You DID do backups right?)

If you don't have everything backed up you'll have to boot from the LiveCD and backup everything in /home first.  Make sure you get all the .filename hidden files and directories.

If starting from scratch, consider making a separate partition for /home if you don't already do so

Chris.

---

### Post by chmmr on 2011-04-29
[https://answers.launchpad.net/ubuntu/+question/154769](https://answers.launchpad.net/ubuntu/+question/154769)

As explained here, I did not need to reinstall from scratch to get working again.  Hope this helps.

---

### Post by DayLite on 2011-04-29
> **chmmr said:**
> [https://answers.launchpad.net/ubuntu/+question/154769](https://answers.launchpad.net/ubuntu/+question/154769)

As explained here, I did not need to reinstall from scratch to get working again.  Hope this helps.

Thanks, I followed your suggestion, Unity desktop came up and I can only do partial upgrades. My program, [Calibre won't work ]("http://ubuntuforums.org/showthread.php?p=10741738#post10741738")

Can you advise what I have to do?

---

### Post by DayLite on 2011-04-30
> **fabricator4 said:**
> .  (You DID do backups right?)

  Make sure you get all the .filename hidden files and directories.

Chris.

I don't understand how to do a backup :confused:
I have a 16 GB Flash Drive, how do I backup? How do I unhide files and directories in 11.04?

I have Ubuntu Tweak and chose backup. It didn't allow me time to choose the flash drive, then said it was backed up.  To where did it save the backup???

---

### Post by fabricator4 on 2011-04-30
> **DayLite said:**
> I don't understand how to do a backup :confused:
I have a 16 GB Flash Drive, how do I backup? How do I unhide files and directories in 11.04?

I have Ubuntu Tweak and chose backup. It didn't allow me time to choose the flash drive, then said it was backed up.  To where did it save the backup???

I don't know about Ubuntu Tweak.  To backup up your data to the flash drive:

1. Insert the flash drive.  When it is recognised it will open a file manager window for it.  If you want a folder on this flashdrive to keep the backup files in, you can make one - right click, create folder.  Then double click on the new folder to open it.

2. Click on the Places -> Home Folder and it should open your home folder.  Press <ctrl><h> and it will unhide everthing.  Press <ctrl><a> and it will mark everthing (for copying).  

3. Now just drag an icon from the home folder to the new folder on the flash drive.  Everything else will come with it as they are all marked. If you fumble it you will lose the "mark all" - if so repeat <ctrl><a>. 

4. Check the sizes of the home folder and the backup folder and make sure they are the same. - If they're not then you missed something.

Chris.

---

### Post by DayLite on 2011-04-30
> **fabricator4 said:**
> I don't know about Ubuntu Tweak.  To backup up your data to the flash drive:

1. Insert the flash drive.  When it is recognised it will open a file manager window for it.  If you want a folder on this flashdrive to keep the backup files in, you can make one - right click, create folder.  Then double click on the new folder to open it.

2. Click on the Places -> Home Folder and it should open your home folder.  Press <ctrl><h> and it will unhide everthing.  Press <ctrl><a> and it will mark everthing (for copying).  

3. Now just drag an icon from the home folder to the new folder on the flash drive.  Everything else will come with it as they are all marked. If you fumble it you will lose the "mark all" - if so repeat <ctrl><a>. 

4. Check the sizes of the home folder and the backup folder and make sure they are the same. - If they're not then you missed something.

Chris.

:)Thanks, I put it on my External Drive, it was 17,085 items and 5.7 GB.

---

