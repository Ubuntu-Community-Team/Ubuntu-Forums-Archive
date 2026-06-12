---
title: "Fresh ubuntu install won't boot?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by VortexTotheFuture on 2010-05-12
So i installed ubuntu 10.04 on my hp laptop within a windows 7 home install. I reboot, finish the ubuntu install, then go back and reboot again to give it a test. I pick ubuntu from the bootloader, then im prompted to pick the kernel (i think thats what it is anyway) so i pick linux 2.6.23-22 and i get this screen

[IMG]http://i971.photobucket.com/albums/ae198/Hazardous420/IMG00005-20100512-2243.jpg[/IMG]


Im a total noob at linux and i dont have the slightest clue what any of that means, can someone please help? I tried re-installing and got the same message

---

### Post by VortexTotheFuture on 2010-05-13
could it be an issue with the install package?

---

### Post by Kevanx on 2010-05-20
Yikes. It looks as though you're not the only one, as I found someone in the forums who updated, and had a similar error. The important line is "Filesystem check or mount failed", meaning that it couldn't mount your new install.

Probably, there's a problem with how the partitions have been made, but the install CD that you made could have been glitchy (it happens on occasion).

My suggestions:
1. Download and burn a new live CD, boot from it, and reinstall from scratch. Double check that you've got the right version, i.e. 64-bit only if you have a 64-bit architecture for your processor. If your computer can handle Win7, it's surprising that you're having trouble booting linux. Be sure to back things up before changing anything with the existing partitions.
2. You can do this while you're reinstalling, but make sure you've got things partitioned appropriately for linux, i.e. "x" Gb for Windows7 (NTFS file system), "Y" Gb for Linux (ext3 file system) , "z" Gb - for Swap (linux-swap). There are great tutorials online, and on these forums, of how to partition for linux with a dual-boot, and partitioning is a default part of the installation process for Ubuntu, or you can open a terminal (Gnome Menu > Applications > Accessories > Terminal) and type:
```
sudo gparted
```

If that reinstall doesn't work, and you have partitions as above, let me know and we'll investigate your mount points.

---

### Post by Linux_junkie on 2010-05-20
Before you attempt to install check to make sure the LiveCD works by running Ubuntu from the liveCD.  If it runs without problems it will install without problems.

---

### Post by VortexTotheFuture on 2010-06-13
I ran the install through a virtual drive using the iso file initially (which gave me the pictured result)

Then i burned it to a cd and gave it another shot, and same results.

Im wondering if HP may have something which "disagrees"  with linux?

---

### Post by Jakiejake on 2010-06-13
> **VortexTotheFuture said:**
> So i installed ubuntu 10.04 on my hp laptop within a windows 7 home install. I reboot, finish the ubuntu install, then go back and reboot again to give it a test. I pick ubuntu from the bootloader, then im prompted to pick the kernel (i think thats what it is anyway) so i pick linux 2.6.23-22 and i get this screen

[IMG]http://i971.photobucket.com/albums/ae198/Hazardous420/IMG00005-20100512-2243.jpg[/IMG]


Im a total noob at linux and i dont have the slightest clue what any of that means, can someone please help? I tried re-installing and got the same message

Hi,
Welcome to Ubuntu and the Ubuntu Forums
Just A few questions
Is it the 32 or 64 bit version of Ubuntu?
Could we please have the laptop model
Is their any important information (documents music etc) on the HDD (Hard Drive)?
What options do you get when you turn the PC on?

---

### Post by VortexTotheFuture on 2010-06-13
> **Jakiejake said:**
> Hi,
Welcome to Ubuntu and the Ubuntu Forums
Just A few questions
Is it the 32 or 64 bit version of Ubuntu?
Could we please have the laptop model
Is their any important information (documents music etc) on the HDD (Hard Drive)?
What options do you get when you turn the PC on?

its the 32 bit version of linux, however the windows 7 install 64 bit (dont know if that really matters...)

the laptop is an hp pavilion dv7 with an intel i7 and an nvidia geforce 230 gt

Theres not really anything important on the hd, but id like to avoid a factory reset or format

After choosing linux as the operating system I get a choice of 2 linux kernels, one marked for recovery the other just regular, then there are 3 more choices, two for windows 7 boots, and a vista one

---

### Post by wilee-nilee on 2010-06-13
> **VortexTotheFuture said:**
> its the 32 bit version of linux, however the windows 7 install 64 bit (dont know if that really matters...)

the laptop is an hp pavilion dv7 with an intel i7 and an nvidia geforce 230 gt

Theres not really anything important on the hd, but id like to avoid a factory reset or format

After choosing linux as the operating system I get a choice of 2 linux kernels, one marked for recovery the other just regular, then there are 3 more choices, two for windows 7 boots, and a vista one

If your still having problems post the script in my sig notice the code tag instructions as well.

---

### Post by Jakiejake on 2010-06-25
Bump!

---

### Post by VortexTotheFuture on 2010-06-28
I've been really busy over the past couple weeks but heres the big news


[drum roll]

it still wont boot....


What exactly am I supposed to do with the script in your sig?

---

### Post by VortexTotheFuture on 2010-07-12
bump...

---

### Post by VortexTotheFuture on 2010-08-09
Whats the script for?

---

