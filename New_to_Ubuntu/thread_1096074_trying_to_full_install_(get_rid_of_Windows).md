---
title: "trying to full install (get rid of Windows)"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by 2roombas on 2009-03-14
Hi.. I have my laptop currently set to dual-boot but have decided to get rid of windows on there all together. Just love this ubuntu! I have nothing in windows on that laptop, never even use windows anymore, so I have zero reason to keep that os.

Yes I have searched the directions and it just doesn't seem to be doing what I'm reading it should by using the Live cd. Why am I just coming to the dual-boot screen after I reboot with the live cd in the drive?  Shouldn't I see a screen asking me if I want to full install?

---

### Post by jordilin on 2009-03-14
Configure BIOS to boot first from cd drive. Then with the live cd you will be able to boot an Ubuntu from memory and then install it permanently on hard drive.

---

### Post by Bucky Ball on 2009-03-14
Down load the Gparted ISO from here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Make a cd and boot from that. You should be able to delete your Windows partition and extend you Ubuntu one.

Failing this, boot the Windows cd, delete all the Windows partitions and exit. Then boot from the Gparted CD and extend your Ubuntu partition into the free space. :) Hope that helps.

The other possibility is to reinstall Ubuntu (are you running 8.04.2?).

---

### Post by Bucky Ball on 2009-03-14
Jordilin,

> **2roombas said:**
>  I have my laptop currently set to dual-boot 

The OP is not running Ubuntu Live CD but as you say, that is the go; mash delete or F1 or whatever key gets you to the BIOS and change the first boot device to CD, hit F10 to save and restart.

---

### Post by 2roombas on 2009-03-14
And I do that, how? :confused:

---

### Post by jordilin on 2009-03-14
](*,) yep, you should use a partitioner, delete the windows partition and use that empty partition for better things.:mrgreen:

---

### Post by Bucky Ball on 2009-03-14
> **2roombas said:**
> And I do that, how? :confused:

Which bit?

---

### Post by jordilin on 2009-03-14
well, actually you can install gparted in your current Ubuntu installation and delete windows from there.

---

### Post by Bucky Ball on 2009-03-14
True, but assuming Windows is on the first partition, when you create a partition to fill the free space you will be creating a primary drive outside the extended partition, if it is set up that way, which is fine but not ideal. Or you could extend your existing Ubuntu partition to fill the empty space, but it needs to be unmounted to do so which is why you need to use the Live CD or the Gparted CD. :)

---

### Post by theozzlives on 2009-03-14
Be sure to give your root (/) partition  the boot flag. I would use the free space as a seperate /home if you don't already have one. This will help [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").

---

### Post by 2roombas on 2009-03-14
> **Bucky Ball said:**
> Jordilin,



The OP is not running Ubuntu Live CD but as you say, that is the go; mash delete or F1 or whatever key gets you to the BIOS and change the first boot device to CD, hit F10 to save and restart.

Pressing f1 right after pressing the "on" still takes me to the os choices screen?!

---

### Post by 2roombas on 2009-03-14
I quite honestly would prefer doing this bios thing since I have the live cd right here.  That gparted thing sounds complicated. This is the "Beginners" section, yes? :)

---

### Post by 2roombas on 2009-03-14
Got it fixed..  thank you! :)

---

### Post by Bucky Ball on 2009-03-14
> **2roombas said:**
> Got it fixed..  thank you! :)

If you managed to download and burn a Ubuntu cd, downloading and burning Gparted is exactly the same. It is just the partitioner from the Live CD and saves a bit of time, that's all. Pretty simple. :)

---

### Post by presence1960 on 2009-03-14
> **2roombas said:**
> Hi.. I have my laptop currently set to dual-boot but have decided to get rid of windows on there all together. Just love this ubuntu! I have nothing in windows on that laptop, never even use windows anymore, so I have zero reason to keep that os.

Yes I have searched the directions and it just doesn't seem to be doing what I'm reading it should by using the Live cd. Why am I just coming to the dual-boot screen after I reboot with the live cd in the drive?  Shouldn't I see a screen asking me if I want to full install?

If you want to create another ext2 or 3 partiotion from the windows partition you don't need the Live CD. Fire up gparted and delete the windows partition and create a new partition. If gparted is not installed open a terminal : ```
sudo apt-get install gparted
```
Then open gparted (will show as partition editor under Administration).

But if you want to delete windows and add that space to your current Ubuntu partition then you must use the Live CD because you can not change mounted partitions.

---

### Post by 2roombas on 2009-03-14
Thank you, but it's fixed now.  I was able to do that bios thing and boot the cd.  Both my mini and my laptop are "pure" ubuntu now, no more windows.  As soon as I add more memory to my old desktop here, it too shall become a Linux convert. :D.

---

### Post by presence1960 on 2009-03-14
> **2roombas said:**
> Thank you, but it's fixed now.  I was able to do that bios thing and boot the cd.  Both my mini and my laptop are "pure" ubuntu now, no more windows.  As soon as I add more memory to my old desktop here, it too shall become a Linux convert. :D.

Glad to hear that!

---

### Post by Bucky Ball on 2009-03-15
Nice work. :)

---

