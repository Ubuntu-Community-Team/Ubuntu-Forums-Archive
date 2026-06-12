---
title: "Ubuntu 10.10 LiveUSB loading problem"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by fubuloubu on 2010-10-10
Hey all,

So I'm new to the whole linux thing and I decided I wanted to give Ubuntu a try on my new desktop I just recently bought. I'm trying the 10.10 64-bit release (which was released today) and I have a problem making it past the POST screen.

Currently, my system is hanging at this line (directly after it finishes POST):

SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al
_

it just sits there and blinks the little underscore character. I've been having issues with the 10.04 distros of Ubuntu and Kubuntu that I've also been running live, but I was able to resolve them by appending 'xforcevesa' to the GRUB boot entry... but I digress. This time it didnt even make it to that screen for me to edit anything, so I wanted to know if anyone had a clue as to what could be broken. 

Thanks in advance.

---

### Post by Rubi1200 on 2010-10-10
Welcome to the forums :-)

How did you put the image on the USB?

---

### Post by JackNocturne on 2010-10-10
Did you use **USB** disk creator?

---

### Post by Hippytaff on 2010-10-10
I'm having the same problem with unetbootin

---

### Post by Rubi1200 on 2010-10-10
I don't know about issues with 10.10 and UNetbootin, but the release notes for Maverick do mention this:

> **It is not possible to create Ubuntu 10.04 USB disks from the  Startup Disk Creator in Ubuntu 10.10 due to a backwards incompatibility  in the syslinux program.**
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications)

---

### Post by C.S.Cameron on 2010-10-10
Have you checked MD5SUM?

---

### Post by fubuloubu on 2010-10-10
I created the boot using PendriveLinux. Tried it with 2gigs persistance, then with no persistance (not sure what it does). no change after an hour either.

---

### Post by fubuloubu on 2010-10-10
> **C.S.Cameron said:**
> Have you checked MD5SUM?

No idea what I'd check with that. It's all in hex.

Rubi1200, that seems more along the lines of what I'm talking about. Did you install using a burnt CD?

---

### Post by Rubi1200 on 2010-10-10
> **fubuloubu said:**
> No idea what I'd check with that. It's all in hex.

Rubi1200, that seems more along the lines of what I'm talking about. Did you install using a burnt CD?
I am not using 10.10 at this stage.

Burning to CD would be my first recommendation though.

---

### Post by JackNocturne on 2010-10-10
Use **USB-**Disk creator and follow with solution from [http://ubuntuforums.org/showthread.php?p=9948797](http://ubuntuforums.org/showthread.php?p=9948797)

---

### Post by Rubi1200 on 2010-10-10
> **JackNocturne said:**
> Use **USB-**Disk creator and follow with solution from [http://ubuntuforums.org/showthread.php?p=9948797](http://ubuntuforums.org/showthread.php?p=9948797)
Would you care to share how you figured this to be the solution and will it work regardless of the user's computer specifications?

---

### Post by Quackers on 2010-10-10
Checking the MD5 checksum will confirm whether or not your downloaded iso is complete and working.

---

### Post by fubuloubu on 2010-10-10
> **JackNocturne said:**
> Use **USB-**Disk creator and follow with solution from [http://ubuntuforums.org/showthread.php?p=9948797](http://ubuntuforums.org/showthread.php?p=9948797)

Didnt work. changing the code in syslinux.cfg as follows:

"Go to root of USB flash disk to the folder /syslinux and find the file syslinux.cfg

Edit the file with a text editor; under the line 

Code:
ui gfxboot bootlogo
change to 
Code:
gfxboot bootlogo
then save."

caused a crash:
Unknown keyword in configuration file: gfxboot

---

### Post by fubuloubu on 2010-10-10
> **Quackers said:**
> Checking the MD5 checksum will confirm whether or not your downloaded iso is complete and working.

okay, well.... which entry should I be checking? its like 15kb of hex and file names.

---

### Post by fubuloubu on 2010-10-10
> **Rubi1200 said:**
> I am not using 10.10 at this stage.

Burning to CD would be my first recommendation though.

Gave up trying to use the USB and burned to CD.

It seems to be working! (despite how sloooooww my cd drive is)

---

### Post by cariboo on 2010-10-10
If you use the latest Windows version of unetbootin you can successfully create a usable usb boot disk.

---

