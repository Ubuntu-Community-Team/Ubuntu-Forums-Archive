---
title: "help unistalling ubuntu"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by ace15225 on 2009-03-03
i recently installing  ubuntu 8.10 on my second HD  and my mom flipped out and wants it out, my friend warned me now to do it via the program list on windows, cause he did that and got a bunch of GRUB errors. but he had no idea how to do it right, any help?

---

### Post by charliehorse55 on 2009-03-03
> **ace15225 said:**
> i recently installing  ubuntu 8.10 on my second HD  and my mom flipped out and wants it out, my friend warned me now to do it via the program list on windows, cause he did that and got a bunch of GRUB errors. but he had no idea how to do it right, any help?

Your mom doesn't know what linux/Ubuntu is. Maybe if you explain to her what it is, she will be okay with it. 

If you just installed Ubuntu on a separate hard drive, you should just be able to format it back to NTFS/FAT32. If you installed it using Wubi, I would recommend reading about it here: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by Bölvaður on 2009-03-03
1. you are unable to uninstall an operating system.. it's either there or isn't.

What I guess you are looking for is let grub go of the master boot record

As I really like grub and dont use windy I can not help you further than this:
[click this link]("http://www.google.is/search?hl=is&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=WjC&q=mbr+windows&btnG=Leita&lr=")

---

### Post by literain2009 on 2009-03-03
You can uninstall ubuntu using a low level formatting or you can use windows manage storage device to detect the partition delete it and recreate. Then edit the autoexec.bat for the booting option -that is if your using it as a dual booth OS.I hope that helps.

---

### Post by oldsoundguy on 2009-03-03
IF this is on a second drive as stated, and there is NOTHING on the drive other than the Ubuntu install .. format that thing.
IF this is on a PARTITION of it's own on that second drive, use gparted from the live disk and remove the partition. (you will find that under system> administration> partition editor.)

Apparently your mom has been reading the MS issued FUD about Linux about how it is spyware and hackers only software and dangerous.  And until you hit your 50's she will never even THINK of listening to anything you say and think it is important if it goes against her mind set!

Get your own box .. you can do anything your heart desires to that one.  (you may have to learn the phrase: "do you want fries with that?" in order to get the bucks.  BUT, it will be YOURS!)

---

### Post by ace15225 on 2009-03-03
lol my mom knows nothing about ubuntu or linux, thats the problem, shes afriad of change, i figured leaving vista on there would be enough for here, but even having to choose her OS at startup was enough to make me take it off, thanks for the help

---

### Post by oldsoundguy on 2009-03-03
My mom had problems with a CORDLESS PHONE and the TV Remote!  It took me MONTHS to convince her that having a computer IN THE HOUSE (not in the garage or basement) would NOT bring a virus into the house.  She heard about computer virus on some program on the toob, and she was bound and determined NOT to let it loose in the place.  (thing is, it was MY place and I was caring for both of my parents .. but had to let her think it was HER place for the sake of MY sanity!)

---

### Post by navaneethan on 2009-03-03
> **ace15225 said:**
> i recently installing  ubuntu 8.10 on my second HD  and my mom flipped out and wants it out, my friend warned me now to do it via the program list on windows, cause he did that and got a bunch of GRUB errors. but he had no idea how to do it right, any help?

> **oldsoundguy said:**
> My mom had problems with a CORDLESS PHONE and the TV Remote!  It took me MONTHS to convince her that having a computer IN THE HOUSE (not in the garage or basement) would NOT bring a virus into the house.  She heard about computer virus on some program on the toob, and she was bound and determined NOT to let it loose in the place.  (thing is, it was MY place and I was caring for both of my parents .. but had to let her think it was HER place for the sake of MY sanity!)

you can uninstall ubuntu inside windows then you have to fix the windows GRUB

by giving the command

 put windows CD then go to repair option after giving  administrator password  you have to enter **fixboot C**: and **fixmbr** then you can reboot you will get ur XP or vista

[here]("http://navaspot.wordpress.com") ask detaily

---

