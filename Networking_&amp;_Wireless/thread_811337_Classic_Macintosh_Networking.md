---
title: "Classic Macintosh Networking"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by cablemouse on 2008-05-29
Hi, everyone I'm new to the forum, so if there is a post similar to mine, please forgive me.

I have somewhat of a weird question:

I have a Pizza Box Mac [Mac LC III] that is running Mac OS 7.6 and has all of the Apple Talk drivers and networking drivers. The internet even works on it lol. Anyways, here is my question. I have some old files on it that I would like to get off it. Is there some way that I can get Ubuntu to read the shared folders from the Mac so I can dump them on my PC?

This model Mac is from about 1993 so it has no USB just a SCSI for external devices - which I don't have any SCSI devices. I don't have a Floppy Disk drive on my PC at all so that method won't work.

Thanks in advance for your help.
Any help would be really appreciated.

---

### Post by thezood on 2008-09-01
This is something that would be very interesting for me too. I recently got my brother's old Macintosh Classic that I thought I'd use for writing (since there would be no temptations to distract me on such an old computer) but I need to be able to have it communicating with my PC first. Haven't found any viable options though, short of buying a usb floppy disk drive and some disks for my PC, which I consider cheating. 

Surely someone with some programming skills should be able to like emulate appletalk via the serial port or something?

---

### Post by loboc on 2008-09-02
apt-cache search netatalk

Description: AppleTalk user binaries
 Netatalk is an implementation of the AppleTalk Protocol Suite for
 BSD-derived systems.  The current release contains support for
 EtherTalk Phase I and II, DDP, RTMP, NBP, ZIP, AEP, ATP, PAP, ASP, and
 AFP.

---

### Post by loboc on 2008-09-02
Heres a blog post with a how to to do the file sharing
[http://www.anders.com/words/netatalk.html](http://www.anders.com/words/netatalk.html)

Good luck

---

