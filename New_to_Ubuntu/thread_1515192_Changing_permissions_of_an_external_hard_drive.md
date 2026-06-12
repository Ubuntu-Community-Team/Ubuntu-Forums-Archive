---
title: "Changing permissions of an external hard drive"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Aube on 2010-06-22
Hello everyone,

Here is my first super-noob message on this lively forum. 
As warmed in the beginner advices section, I won't be afraid of asking very basic question but I just would like to let you know that my knowledges of Linux are very, very poor thus I may really need patient people to explain my step by step how to deal even with the most basic issues. To say it simply, the "terminal" is something scary for me and I still haven't used it :roll:

First my computer :
(not sure if it is necessary here, but) on the same internal hard drive, two partitions, one with Ubuntu, the other with Windows Xp.
I always put my personal data on a external hard drive, so that it allows me easily to use them regardless the operating system I am using.

My problem is that when I connect this external hard drive to friends' computers to get files like pictures from them, my external hard drive refuses to copy anything. In other words, I can give files to my friends' computers but can not write anything from them to my external hard drive. I checked the permissions both on Ubuntu and Windows and it seems that it is set as 'read only'. My great problem is that I cannot change this status, even if I'm the admin.
I tried of course to search for similar issues on the forum before posting but did not find something helpful or above all understandable considering my very beginner level.
I am not sure if my hard drive is NTFL, or another obscure status :) but would be pleased to know how to check that too ;)

So thank you very much for any patient help ! I'm leaving Japan very soon after one year of exchange and can't leave without getting all the nice pictures I had with my friends.
Thank you ;)

---

### Post by S.R on 2010-06-22
Is your external format all NTFS or EXT3? Sounds like a file system format problem. 

Seeing you are from BRU has me longing for shawarma from Cappadocia on Boulevard Adolphe Max.

---

### Post by k3lt01 on 2010-06-22
[Try this]("http://ubuntuforums.org/showthread.php?t=1037634") to see if it is any help

---

### Post by mikewhatever on 2010-06-22
If you haven't changed it, the file system is either FAT32 or NTFS. Try running the file system check on that hdd in Windows.

---

