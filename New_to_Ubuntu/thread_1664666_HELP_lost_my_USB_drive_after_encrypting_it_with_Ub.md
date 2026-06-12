---
title: "HELP lost my USB drive after encrypting it with Ubuntu &quot;Disk Utility&quot;"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by sarc on 2011-01-11
Got a new USB drive (Transcend 500Gig), I reformatted from FAT32 to EXT4 using 'Disk Utility' in Ubuntu 10.04 Administration menu.  The Utility gave me an option to encrypt it, I chose yes, provide password and formatted.  Everything worked fine and I used the drive, but after 1st reboot it does not show on my desktop or in 'Disk Utility'.  If I open Truecrypt (I use it for other folders) Truecrypt sees the drive but cannot mount it.  
GParted sees it correctly as File System 'crypt-luks' but does not offer me an option to mount it.

Do I need another application to open my drive?  Can I auto-mount it somehow (still providing password of course)  Help!

---

### Post by sarc on 2011-01-23
Bump bumpity bump!!!!!!!!!!

---

### Post by sarc on 2011-01-27
After trying to leave the drive connected for 15-30 mintues it finally showed up on Disk Utility - it was just that Ubuntu wanted to scan the whole drive once before showing it in connection.
So now I have a drive but cannot mount it.  I tried downloading the LUCKS tool but it cannot open it - it says 'Unable to open blah blah... probably a Truecrypt volume' (I did try to open it with Truecrypt once but it failed).

So now I can see my drive but no idea how to mount it.  Anyone....?

---

### Post by HermanAB on 2011-01-27
Howdy,

First you need to know what encryption system was used on it.  It can be LUKS or encfs. It likely won't be truecrypt.

Here is a guide that may help you undestand LUKS:
[http://www.aeronetworks.ca/howtos/luks-usb-howto.html](http://www.aeronetworks.ca/howtos/luks-usb-howto.html)

---

### Post by sarc on 2011-01-27
Thanks - I'm prety sure Disk Utility said algorithm was AES, and my bet is using LUKS.
Jeepers Disk Utility is a utility that came with default installation of Ubuntu 10.4... anyone has info?
I'm resigned to reformat tomorrow if I can't access the darn thing.

Cheerio

---

