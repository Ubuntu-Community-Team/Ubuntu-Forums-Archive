---
title: "Backing up Windows before first Ubuntu install."
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Citizen Snips on 2010-06-27
Hello. :)
I'm currently running Windows XP and was planning on switching to Ubuntu today. Have it downloaded and ready to go. Before I install, though, I wanted to back up Windows to CDs. My computers OEM from Sony, no recovery discs or XP installation disc and, for some reason, there's no back-up program in my 'Accessories' folder. As far as I know, there's a hidden back-up partition on my hard-drive, but I was hoping to clean that as well. So, after trawling tutorials for half an hour, I'm at a loss. Few questions:


[LIST]
[*]How do I make an external back-up of Windows XP to re-install it, should I ever need to (preferably on CD, but I have an external HDD, too)?
[*]Once I get Ubuntu installed, how do I go about ridding my system of Windows and all its works and all its empty promises? Will my Ubuntu install automatically overwrite Windows?
[*]How can I wipe my Windows recovery drive and regain the space it used?
[/LIST]
I realise this is a slightly inappropriate question as it's not directly Ubunt-related, but I promise I'll be back with more once I get this one over with.

Thanks a million. :D

---

### Post by GreenN00b on 2010-06-27
See this link for backup [http://www.thefreecountry.com/utilities/backupandimage.shtml]("http://www.thefreecountry.com/utilities/backupandimage.shtml")

You can select to partition all hard drive when installing Ubuntu, erasing all other partition(windows partition and hidden backup partition).

---

### Post by nhasian on 2010-06-27
actually prepping your system for ubuntu is totally ubuntu related :)
for backing an entire hard disk, or even individual partitions, i use [Clonezilla]("http://www.clonezilla.org/")

the system restore partition probably doesnt take up much space and if you leave it, it wont bother your ubuntu installation.  then in the future if you ever want to restore to factory defaults (like if your going to resell your computer) it is easy to do.

> **Citizen Snips said:**
> H
I realise this is a slightly inappropriate question as it's not directly Ubunt-related, but I promise I'll be back with more once I get this one over with.

---

### Post by Citizen Snips on 2010-06-27
Thanks for the suggestions. :)
I've already manually backed up stuff I want to keep to my external hard-drive.
I found this [[http://www.howtohaven.com/system/createwindowssetupdisk.shtml]](http://www.howtohaven.com/system/createwindowssetupdisk.shtml]) through GreenNoob'a link and am currently working my way through it. Sounds smart, so I'm gonna go ahead and trust it. :P

---

### Post by jflaker on 2010-06-27
just copy C:\Documents and Setting\YourUserID to an external storage device..........that should get ALL of your data...you can then selectively copy back what you want.

I did this for one of my clients as it was far faster to copy 4.7GB of data than to find all the files hidden all over the user folder and possibly miss something.

You don't need the software as that can all be reinstalled.....unless of course you don't have the install media.

Clonezilla works great too, you just need enough space for the image.

---

### Post by wilee-nilee on 2010-06-27
The backup is okay, but if you want to be sure you can reinstall it at some time buy the OEM install from Sony, these will have the sata drivers. I just bought the XP OEM 3 disc set from Acer for 20$ US

XP needs sata drivers to install and I'm not sure a backup is going to just slide in and work, in other words cover your booty with the OEM discs.

---

### Post by Citizen Snips on 2010-06-27
Thanks, lads.

I made an XP install disc following that tutorial.
Now downloading Clonezilla to back up to my external HD. Might make another backup CD with it, too, just in case.
And then, sure, if I'm stuck, I can buy the OEM discs. Think that'll cover me. :P

---

### Post by Citizen Snips on 2010-06-27
Hmm, I've hit a snag with Clonezilla. Burned it to CD, set BIOS to boot from optical drive, but it's still booting straight to Windows. Any ideas?

I'm gonna call it a night and have another crack tomorrow. Thanks for the help thus far. :)

---

### Post by CharlesA on 2010-06-27
Make sure the MD5SUM checks out and make sure that you created a cd from the image instead of just put the iso on the cd.

---

### Post by Citizen Snips on 2010-07-05
Sorted.
Got Clonezilla running and made a full back-up image on my external HD. Also have the installation CD I made and kept the recovery partition.
Surely, one of those must work.
That said, though, I got Ubuntu installed and, based on my experience thus far, I can't see myself switching back any time soon. :)

Thanks a million for the help, lads. Amazed at the response time and willingness to help.

---

