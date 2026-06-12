---
title: "openSUSE 11"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Aero_Zeppelin on 2010-12-19
Im currently using maverick on my netbook.It has a 160GB HDD and buntu is currently using the entire Hard disk (no partitions).I want to install openSUSE 11 alongside the ubuntu install (dual boot).Is that possible to do without losing my data? Will i have to make another partition for suse?If yes,how do i go about it?I have very little experience with linux,So id be really grateful if you guys could help me out.:)

---

### Post by germanix on 2010-12-19
This would be no problem at all. When you install Suse, the installer will recognize that Ubuntu is installed and will then suggest a certain part of the HDD for its own use. It will normally try to take half of the HDD. You can then decide how much you want to give it and can "drag" the arrows to make the partition bigger or smaller. You will not lose any data but if you want to make 100% sure, make a backup of your data on Ubuntu. (one should always have a backup anyway). When booted into either of the Os`s you will have access to the data of the other.
There are other "better" ways to do it but I suggest you keep it "simple/stupid" for the meantime until you learn more.

---

### Post by amjjawad on 2010-12-19
> **Arindam Momin said:**
> Im currently using maverick on my netbook.It has a 160GB HDD and buntu is currently using the entire Hard disk (no partitions).I want to install openSUSE 11 alongside the ubuntu install (dual boot).Is that possible to do without losing my data? Will i have to make another partition for suse?If yes,how do i go about it?I have very little experience with linux,So id be really grateful if you guys could help me out.:)

Although this thread is marked as "SOLVED", allow me to offer some advices and suggestions.

First thing first, you need to understand that there's a major difference between OpenSUSE and Ubuntu which is the boot loader as OpenSUSE uses GRUB Legacy while Ubuntu uses GRUB2.
GRUB2 is taking the full control now to boot your machine. If you'll install OpenSUSE without even knowing what's going on then you might be in trouble if not now, later on. GRUB2 is much easier to update than GRUB Legacy when it comes to new Linux-Users as most of the cases, you just need to run:

```
sudo update-grub

```
With GRUB Legacy, it's different.

Another thing you need to understand that you need to re-partition your HDD as long as your Ubuntu is using the whole space.
Here's a guide that will be very helpful: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Please, try to read it all.

I could offer the right scheme for you but you need to read and learn what you're going to do. 

Also, it's better to read the release notes for both Ubuntu and OpenSUSE. Just to be familiar with both.

Finally, before you even think to install OpenSUSE, try to create a LiveCD for it and try it without installation. Sometimes, OpenSUSE can't detect certain hardware.

Good luck ;)

---

