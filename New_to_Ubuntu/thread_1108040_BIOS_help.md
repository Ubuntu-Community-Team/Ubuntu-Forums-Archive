---
title: "BIOS help"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by this is new york not l.a. on 2009-03-27
ok so I've been wrestling with this old compaq armada laptop. I'm trying to install dsl on it but it wont install. I was told that I need to make the cd rom boot first instead of my hard drive. however i cannot access my bios at the start. I've tried every key combination possible and I was wondering if I could access bios via ms dos or a command or something. idk if it matters but I'm running win 98 on it. thanks for any replies

---

### Post by philinux on 2009-03-27
From google.

[http://www.annoyances.org/exec/forum/winme/t1003933721](http://www.annoyances.org/exec/forum/winme/t1003933721)

Hold down Function key and F8 then power up the computer keep these keys down and tap F11.

---

### Post by this is new york not l.a. on 2009-03-27
thanks tried that but nothing happens. when i boot up this is whats displayed

32768 kb ok
162-System Options Not Set

The following configuration options were automatically updated:
disk 1 type: 65
total memory installed: 32768 kbytes
coprocessor added
diskette drives
cmos checksum invalid, default values loaded
f1 save changes
f2 ignore changes



if i hit f1 it just loads staight into windows, if i hit f2 it does nothing but go to a black screen

---

### Post by philinux on 2009-03-27
Cant help their then. But you could try installing using unetbootin instead of using the cdrom.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other)

---

### Post by starcannon on 2009-03-27
Which series of Armada is that? I'll dig around and see if I can find the key/combo to get you into the setup/bios.

---

### Post by mhgsys on 2009-03-27
>  starcannon  	
Re: BIOS help
Which series of Armada is that? I'll dig around and see if I can find the key/combo to get you into the setup/bios. 


thats a good question indeed,since the armada 1700's didn't have inbuilt BIOS settings for setup etc.
It had to be installed on the hard drive or run from a floppy disk.
If it's installed on your hard drive you could run the bios setup by pressing F10.

Otherwise you'll have to download the setup from [www.compaq.com](www.compaq.com) and put it on a floppy and run it from there; the floppy created is bootable so your laptop should go straight into the setup.

---

### Post by this is new york not l.a. on 2009-03-27
its a 1450 i believe (its not with me at the moment so i'm not 100% sure)

---

### Post by spcwingo on 2009-03-27
I had one of the Armadas (1592DMT).  They have a partition on the hard drive that is essential to CMOS setup along with a floppy disc that allows you to access the CMOS.  When I received mine the partition was long gone, but thankfully it was already set to boot from CD.  You might be able to do a little digging around on the Compaq site to the CMOS partition image and floppy disc image.

---

