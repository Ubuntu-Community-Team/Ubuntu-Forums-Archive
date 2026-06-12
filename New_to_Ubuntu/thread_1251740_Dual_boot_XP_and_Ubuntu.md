---
title: "Dual boot XP and Ubuntu"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by rob86 on 2009-08-28
I have Windows XP, an Ubuntu cd, one internal 160GB hard drive, one internal 20gb hard drive, and one 500gb External USB drive. I want to install Ubuntu, but I want to keep XP installed. I don't know much about partitions, but I want to keep XP installed where it is (on the primary 160gb drive). I don't care where Ubuntu is, as long as I can boot to XP when I want.  How do I go about doing this? I have very little experience installing OS's and since I lost my XP CD and have no clue where it is, I'd rather to my best to avoid having to reinstall XP so I'm being quite cautious about the whole thing.

---

### Post by MelDJ on 2009-08-28
you should install it with wubi. just boot to windows, put the cd in and select the install inside windows button and follow the instructions.:popcorn:

---

### Post by MelDJ on 2009-08-28
try this link [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by Regenweald on 2009-08-28
Firstly defrag XP. after that you can just boot into the Ubuntu install cd and follow the instuctions. At one point it will find your XP install and ask you what to do, here you can just drag a slider to determine the size of your  disk you want to dedicate to each Ubuntu and XP.

Just take your time, the installer is painless, if at any point you have a concern you can cancel that entire thing and ask questions back here.

---

### Post by Tutigan on 2009-08-28
Wubi is one option... But dual-booting is easy to set up.
Just slap in the livecd and hit install... when it comes to it, resize your XP partition and install Ubuntu on the end (or the other HDD if that's how you want it). GRUB should pick it up automatically, else we can always help with getting XP to show up in GRUB!

---

