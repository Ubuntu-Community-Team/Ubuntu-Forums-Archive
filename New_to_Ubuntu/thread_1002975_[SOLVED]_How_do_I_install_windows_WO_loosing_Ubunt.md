---
title: "[SOLVED] How do I install windows W/O loosing Ubuntu"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by matdombrock on 2008-12-05
I just got an HP 530 notebook. I bought it from an ubuntu user so thats what was on it. He says that he couldn't get Xp to work and neither could his grandma who works as a network administrator. I have a feeling that this hard drive uses SETA witch isn't recognized by Xp.

Really though, my question is:

Is there a way to try installing without loosing my ubuntu install? When I have attempted this in the past I would install windows without loosing my actual ubuntu partition. However i think that the windows boot loader over wrights grub.

Does anyone have some advice to offer me?

---

### Post by taurus on 2008-12-05
You can use either gparted from the LiveCD (desktop CD) or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), to resize your harddrive.  Then, create a primary partition on that unallocated space and format it to ntfs.  Now, just windows CD and install it on that partition.  After installing windows, you need to use the LiveCD to reinstall GRUB to MBR since windows has already overwritten it.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by matdombrock on 2008-12-05
Wow, Thanks for the help! I thinks that I looks a little easier to just install windows and then reinstall ubuntu but i might do that. Thanks again!:D

---

### Post by Keen101 on 2008-12-05
you can alway's reinstall GRUB with this disk. It also functions the opposite way too... if you need to restore the windows MBR, it will put that on there too. Great and useful CD.


[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by MarblePanther on 2008-12-05
I agree with above

That disk has saved my buttocks many times over!!! lol

---

