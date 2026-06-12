---
title: "Big question here"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by EddiePugh on 2010-11-28
I downloaded ubuntu and put it on my usb stick, but when I go to boot it, my computer runs the little dots, at the end it says running, then restarts my computer only to come to the same thing over and over again. This computer is a new Windows 7 laptop, but for reasons unimaginable am not able to load ANY OS besides puppy linux from a cd. Any help is appreciated :)

---

### Post by EddiePugh on 2010-11-28
Is there a way to upgrade from Puppy Linux to Ubuntu?

---

### Post by Rex Bouwense on 2010-11-28
I have to ask.  Did you md5sum the download before you burned the ISO to the flash drive?  Did you change the boot order in your BIOS to boot from the flash drive first.  Try burning the ISO on a CD and booting from that (again change the boot order to boot from the CD drive first).
No.  You cannot change from Puppy to Ubuntu.  Two different OS.

---

### Post by EddiePugh on 2010-11-28
I did not md5sum the download, I have no idea how to do that.

---

### Post by matt_symes on 2010-11-28
Hi

Read these.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Also burn the CD on the slowest speed.

Kind regards

---

### Post by Rex Bouwense on 2010-11-28
OK.  When you download a very large file, you want to be sure that you got the download correct, so you perform a procedure that insures this.  It is called an MD5Sum.  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
The example uses Ubuntu 8.10 so you have to put in the version that you downloaded instead of 8.10.
Once that is done you have to burn the image to a CD or a flash drive to make it bootable.

---

### Post by Rex Bouwense on 2010-11-28
Matt, you beat me to the draw and you got the hash web site.  I couldn't find it.  I got so much stuff bookmarked that I really need to get in there and organize it.  On top of that I'm at a big disadvantage only typing with two fingers.  :D

---

### Post by jcipale on 2010-11-28
Rex has the right idea. When booting up our laptop and you are presented with the 'Hit <F2> to change settings, select the F2 and go to Boot-order. Your USB device should be listed. Follow the instructions to make the USB drive the first boot-device (just as long as it precedes the HDD)

---

### Post by matt_symes on 2010-11-28
Hi

> Matt, you beat me to the draw and you got the hash web site.  I couldn't  find it.  I got so much stuff bookmarked that I really need to get in  there and organize it.  On top of that I'm at a big disadvantage only  typing with two fingers. 

Yes. I just had both sites open for a check i am currently running, so i had bit of a head start there.  :) Ahh, the joys of downloading.

Kind regards

---

### Post by ColdnitroX on 2010-11-28
Also, if you are burning very large files, use the UDF filesystem on the CD. It kinda helps.:grin:

---

### Post by ajgreeny on 2010-11-28
If downloading an .iso file that is large, it is definitely worth using a torrent client.  I have no idea what is available for windows, but there are certainly several, and like all such applications it will check each part of the file as it comes down, and if any parts are faulty it will get that packet again.  This means that the file will certainly be non-corrupt to start.

Following that, it is always worth using the "Check install media" option at the start of the live CD/USB that you use for installing, just to be sure it is OK.

---

