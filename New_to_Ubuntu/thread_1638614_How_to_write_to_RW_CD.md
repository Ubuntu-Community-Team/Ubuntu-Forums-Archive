---
title: "How to write to RW CD"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-05
I want to copy some files from my USB SD card to my RW CD. When I "copy" the files from the card and try to "paste" them on the RW CD, I get a error that I need permission. I know this has to do with sudo or su, can someone tell me how to set up permissions so that I may paste stuff into my RW CD?

---

### Post by uRock on 2010-12-05
When I have done this in the past, I used Brasero. I opened the burner program and selected the files to be burnt to the disk.

---

### Post by ashu. on 2010-12-05
> **uRock said:**
> When I have done this in the past, I used Brasero. I opened the burner program and selected the files to be burnt to the disk.

Ya dude i totally agree u better use Brasero n write almost like using nero in windows...

---

### Post by s1baker on 2010-12-05
In Windows, I don't use a program, simply copy and paste like onto a HD.
How do I get the Bracero program?

---

### Post by Zzl1xndd on 2010-12-05
> **s1baker said:**
> In Windows, I don't use a program, simply copy and paste like onto a HD.
How do I get the Bracero program?

Brasero is installed by default it should be under Applications > Sound and Video.

---

### Post by s1baker on 2010-12-05
I have Bracero and I ran it and went to my SD card to copy a folder with all the files in it to my CD, but I can't see any place to select "copy" in Bracero so that I might burn it to my CD.

---

### Post by Zzl1xndd on 2010-12-05
One Brasero is open select Data Project > From here you can drag files on to the screen(or select the + sign at the top to navigate your folder tree). 

Then click burn.

---

### Post by s1baker on 2010-12-05
I did what you said and I got the message "Do You Really Want To Blank The Disc? the disk in the drive holds data", which I don't, as there is other data on the disk.

---

### Post by s1baker on 2010-12-05
also, I need to mention, the CD now on Ubuntu was a CD that was made on Windows XP using InCD. I can Read and Copy the files ok, but I think this is a Fat32 file CD and Linux will not write to the CD unless it completely wipes it for a clean start. Is this correct?

---

### Post by mcduck on 2010-12-06
Ubuntu doesn't do packet writing, only normal CD's, so you can't add individual files to optical media, not even rewritable ones. You can only write CDs in the normal way (full disk at a time).

I'm not sure if there's any packet writing software available for Linux.

---

