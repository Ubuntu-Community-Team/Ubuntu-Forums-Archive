---
title: "USB boot"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by GigaG on 2010-12-11
I want to add a folder containing files to my live Ubuntu USB, which I intend to use as an emergency system rescue device. Will adding another directory make it unbootable? It is-

Ubuntu 10.10 desktop

2GB Casper-RW

Created with Universal USB Installer by Pendrivelinux

4GB HP v125 USB flash drive

I've attached a picture of the root of the drive. Again. will adding a new directory in the root of the drive make it unbootable?

---

### Post by diablo75 on 2010-12-11
I'm pretty sure the stick will remain bootable, so long as you don't delete anything.

---

### Post by C.S.Cameron on 2010-12-11
You can add a new folder no problem as long as you have room in the root.
You will be able to read and write to this folder when the USB drive is plugged into another O/S.
When you are booting from the USB device you need to go to filesystem/cdrom to find the new folder, it will be read only, (in 10.10).
You should be able write to it if you access it with gksu nautilus.

Edit:
Welcome to the forums.

---

### Post by miegiel on 2010-12-11
The SD card in my camera is a ubuntu live install disk, never caused any problems. I also made a trans (transport) directory on it to copy stuff from one PC to another.

---

### Post by bodhi.zazen on 2010-12-11
When I do this I partition the usb stick. The first partition is then the boot partition , the second is the data partition.

This way i can easily replace the OS and keep the data.

---

### Post by C.S.Cameron on 2010-12-12
> **bodhi.zazen said:**
> When I do this I partition the usb stick. The first partition is then the boot partition , the second is the data partition.

This way i can easily replace the OS and keep the data.

Windows, (which some people still use), will only see the first partition on a flash drive.

---

### Post by bodhi.zazen on 2010-12-12
> **C.S.Cameron said:**
> Windows, (which some backward people still use), will only see the first partition on a flash drive.

Yes I know. There are some advantages to that as well, especially on a portable bootable stick.

---

### Post by amjjawad on 2010-12-12
> **diablo75 said:**
> i'm pretty sure the stick will remain bootable, so long as you don't delete anything.

+1

---

### Post by C.S.Cameron on 2010-12-12
> **bodhi.zazen said:**
> Yes I know. There are some advantages to that as well, especially on a portable bootable stick.

Bodhi:
With all respect, I think GigaG is talking about a persistent install, (thus the 2GB casper-rw file and screen shot).
My experience is that the files must also go on the first partition.
Cork

---

### Post by GigaG on 2010-12-12
Thx guys. I am kinda insulted you just called me "backwards" for using Windows. It is an OK system, it runs all my games, and I'll just use CDs and USB sticks to dip my toes into the world of Ubuntu.

Also, this is unrelated, but when you refer to "beans" on the site, do you mean posts?

---

### Post by amjjawad on 2010-12-12
> **GigaG said:**
> Thx guys. I am kinda insulted you just called me  "backwards" for using Windows. It is an OK system, it runs all my games,  and I'll just use CDs and USB sticks to dip my toes into the world of  Ubuntu.

Please don't be offended, I don't think he meant you specifically.  However, I think that was unnecessary word. Windows users are MUCH more  than Linux users in the whole world. It doesn't mean anything bad. After  all, neither Linux is perfect nor Windows, period.

I hope you don't feel bad about that and hope you accept my apology.


> **GigaG said:**
> but when you refer to "beans" on the site, do you mean posts?

Yes.

---

### Post by GigaG on 2010-12-12
Thanks. I hope I can give some thanks to the community. You are all very nice people.

---

### Post by amjjawad on 2010-12-12
> **GigaG said:**
> Thanks. I hope I can give some thanks to the community. You are all very nice people.

You welcome :)

Hahaha, nice avatar :D

---

### Post by C.S.Cameron on 2010-12-12
> **GigaG said:**
> Thx guys. I am kinda insulted you just called me "backwards" for using Windows. It is an OK system, it runs all my games, and I'll just use CDs and USB sticks to dip my toes into the world of Ubuntu.

Also, this is unrelated, but when you refer to "beans" on the site, do you mean posts?

My apologies GigaG, My humor often escapes a lot of people, I was not referring to just you, I use XP myself at times, in some circumstances it is almost unavoidable.
Please do not report me for abuse:(
Welcome to the forums.

---

### Post by tajiknomi on 2010-12-12
> **C.S.Cameron said:**
> My apologies GigaG, My humor often escapes a lot of people, I was not referring to just you, I use XP myself at times, in some circumstances it is almost unavoidable.
Please do not report me for abuse:(
Welcome to the forums.

[SIZE=2]When i saw your post that time, i feel quite ***strange*** for it... But i just got silent because you are senior and almost know more about OS's[/SIZE], [SIZE=2]but i hope you will not use it again future(with due Respect)[/SIZE] :P [SIZE=2]i Hope you will not mind as well as OP,[/SIZE]

---

### Post by bodhi.zazen on 2010-12-12
> **C.S.Cameron said:**
> Bodhi:
With all respect, I think GigaG is talking about a persistent install, (thus the 2GB casper-rw file and screen shot).
My experience is that the files must also go on the first partition.
Cork

I think we are sort of talking apples and oranges. If you make a data partition you can mount it with a persistent install.

---

