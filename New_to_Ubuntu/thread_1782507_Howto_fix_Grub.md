---
title: "Howto fix Grub?"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by shareMenaPeace on 2011-06-14
Hi, 
i just had to install windows 7 on another partition and now i cannot boot ubuntu anymore.
When i launch the CD i used to install ubuntu 10.10 i can only choose to "install ubuntu" the boot from first hard disk, boots windows.
Also i got an older version of Super Grub Disk, but which only gives errors!

How do i know if i got Grub 1 or 2?


So any tips how i can fix the boot of ubuntu grub? 

Thanks!

---

### Post by Quackers on 2011-06-14
What dvd is that please? Is it an Ubuntu live cd but on a dvd?

---

### Post by JohnBonne on 2011-06-14
I am having the same problem. In fact this is probably a milestone for Linux based systems. I am subscribing to this thread. 

Good Luck,

---

### Post by cipherboy_loc on 2011-06-14
Run the boot info script that I have a link to in my signature, and attach the resulting results.txt file, or wrap the results (Copy+paste into the post) in code tags.

---

### Post by shareMenaPeace on 2011-06-14
I testing Rescatux now [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


> **Quackers said:**
> What dvd is that please? Is it an Ubuntu live cd but on a dvd?
I use Ubuntu 10.10 64 bit version, sorry i don't know if this is a "Live CD", Note it is a "CD"

---

### Post by Quackers on 2011-06-14
> **shareMenaPeace said:**
> I testing Rescatux now [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)



I use Ubuntu 10.10 64 bit version, sorry i don't know if this is a "Live CD", Note it is a "CD"

Could it be server edition or alternate installer cd? If so, no live system. You could always download the 10.10 desktop system and make a cd. Then you can boot from that and re-install grub very easily.

---

### Post by shareMenaPeace on 2011-06-14
> **shareMenaPeace said:**
> I testing Rescatux now [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Rescatux 0.27 just  says there is an error during install. Very strange it ask me several times about partition ordering, but i think i set it correct.

> **Quackers said:**
> Could it be server edition or alternate installer cd? If so, no live system. You could always download the 10.10 desktop system and make a cd. Then you can boot from that and re-install grub very easily.

Ok i booted from another CD which is a "Live CD" i booted into Ubuntu. Now how can i easily restore Grub into the MBR?

Thanks

---

### Post by Quackers on 2011-06-14
The live cd needs to be at least 10.04 iirc.
You also need to identify which partition your Ubuntu root is on. You can use sudo fdisk -l in the terminal or open gparted and look.
Once you identify that you should run the following commands, putting your root partition in the first command (eg /dev/sda5) and your first boot hard drive in the second (eg /dev/sda).
```
sudo mount /dev/sdXY /mnt  
sudo grub-install --root-directory=/mnt /dev/sdX
```

---

### Post by shareMenaPeace on 2011-06-14
I had to change the keyboard layout, in order to write "/".

So the partition i want to boot is "/dev/sdb5/" for linux. The "dev/sdb5" is extended under "/dev/sdb3"
And "/dev/sdb2" for windows.  

Could someone be so kind and write the code for this, because i'm not sure if i understand Quakers description. Thanks

---

### Post by Quackers on 2011-06-14
No problem.
Your first command should be ```
sudo mount /dev/sdb5 /mnt
```
The second command depends on a couple of things. 
Where do you want grub to be installed? To the mbr of the first bootable hard drive would be normal. If /dev/sda is the hard drive that your bios boots first, then that's where you would install grub to. If that drive is /dev/sdb then that's what you would put in the second command.

How many hard drives have you got connected and which one is set to boot first in your bios? Is that where you want grub to be installed?

---

### Post by shareMenaPeace on 2011-06-14
```
sudo mount /dev/sdb5 /mnt  
sudo grub-install --root-directory=/mnt /dev/sdb
```
Finally i was able to restore Grub, with above code^^

Thank you all!

---

### Post by Quackers on 2011-06-14
Aha! That's good then :-)
I see /dev/sdb boots first then.

---

### Post by shareMenaPeace on 2011-06-14
> **Quackers said:**
> Aha! That's good then :-)
I see /dev/sdb boots first then.

Yes somehow it does the trick. Actually i don't know which HD is set how in bios, but this works! :) Ah this is so good to see ubuntu again! (Plus all my files!)

---

### Post by Quackers on 2011-06-14
Don't forget to run ```
sudo update-grub
``` to get the Windows Loader back in the grub menu :-)

---

### Post by shareMenaPeace on 2011-06-14
> **Quackers said:**
> Don't forget to run ```
sudo update-grub
``` to get the Windows Loader back in the grub menu :-)
Ok, i did this. It found some files and it seems all went fine!

---

