---
title: "[SOLVED] Ubuntu server, Windows XP Client (FAT32) File/print sharing"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by Purplecatty on 2007-10-16
I have Ubuntu box as a Print server.  It aslo can share with XP Client boxes including wireless laptop (All XP Client drives are NTFS).  Ubuntu Box was a Feisty Fawn 7.04.  It worked like charm.  Also I had to convert file system on my Laptop from Fat32 to NTFS so that It can work with Ubuntu box (So it can "see" and share each other even printer sharing).  I noticed the pattern,  Whenever I reinstall XP OS on my laptop (Acer Aspire 5040 wlmi) which is originally FAT32 on XP at factory level, It can "see" Ubuntu box but unable to log in to get in file.  So did my Ubuntu box can "see" Acer but cannot log in to get in file.  I had to convert Acer laptop's drive to NTFS and it finally became "passive".   

(MY laptop's Restoration DVD been burnt to back up it's original Windows XP.  I can't do much on file in DVD { like hacking it and change FAT32 to NTFS and burn another DVD w/ NTFS so that when restoring XP OS, it would be NTFS instead of FAT32. }  It's a compressed file and I'm not an expert on that..) 

What happen is that my laptop got mess up again (after 3 months of usage).  I had to reinstall XP OS and it's back on FAT32..  I didn't feel like converting it back to NTFS.  Also I upgraded Ubuntu box to Gusty Gibbon 7.10 beta.  The problem still remains between Ubuntu Server and Acer XP Client. :confused:  Ubuntu box are able to "see" and manage files on other XP box Client with NO Problem cuz XP Box drive is a NTFS..  

So Question is that How do I get Ubuntu box to talk to Laptop XP Client w/ FAT32 and be "Passive"??  Also to have Laptop XP Client to be able to use Ubuntu's printer..](*,):-k

I would greatly appreciate for your suggestion or answers!!

Thanks
Catty

---

### Post by Purplecatty on 2007-12-02
Never mind!

Found the problem.  It's the Windoz laptop's Zonealarm Internet Security suite.  It blocked incoming port!!  So I decide to uncheck it and finally got through!! Now everything else including Ubuntu Printserver worked!!

---

