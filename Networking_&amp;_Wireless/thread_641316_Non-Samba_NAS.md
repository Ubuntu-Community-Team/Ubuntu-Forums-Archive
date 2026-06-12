---
title: "Non-Samba NAS?"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Skyoodpov on 2007-12-15
I hope this is an appropriate location to post for this...

I want to add a Network Attached Storage device to my home network, specifically for hosting my music and movies.

I have had A LOT of issues trying to get most linux music players to see my MP3 collection when shared over a windows network share.  Amarok HATES windows network shares...

Has anyone found a NAS enclosure that I would be able to map as a Linux share?

I am considering running FreeNAS on an old laptop, but I would rather use a nice clean enclosure if one exists.  Less power consumption, etc...

Thanks in advance

---

### Post by jetsam on 2007-12-15
From what I understand, you may have a hard time finding a NAS that ISN'T samba based.

Samba, per se, isn't really a problem though.  You should be able to mount samba shares through the cifs filesystem either manually or in your fstab.  This will make Amarok happy-- I use it daily through cifs mounted shares from a Samba fileserver.  

Here are two how-to's on mounting shares through cifs:
[http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")
and
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

Which NAS devices are Ubuntu friendly is a different question, though.  I wish there was a good run-down somewhere on this.  I ended up giving up on the question and putting together a cheap fileserver because I didn't like the idea of being stuck with some NAS company's firmware.

---

### Post by HermanAB on 2007-12-15
Hmm, if you buy it, then it is going to be Samba based.  However, you can use any old PC, stuff it full of disk drives, install Linux with either Samba, NFS or FTP servers and make your own NAS.

If you wish to go pointy-clicky, then FreeNAS is a good idea, otherwise Mandriva or PCLOS.  (The Ubuntu wizards are really rather basic and not particularly good at setting up this type of thing, whereas Mandriva has very good wizards for *everything*.)

Cheers,

Herman

---

### Post by Skyoodpov on 2007-12-16
Thanks for the help all! 

I will probably set up either a simple sharing laptop (I have an ancient Dell I can conscript for duty),  or give FreeNAS a try.  Hopefully one way or another I can get a simple wake-on-lan setup going.  I want this thing to be readily available at all time, but hopefully without having to be ON all the time.

---

