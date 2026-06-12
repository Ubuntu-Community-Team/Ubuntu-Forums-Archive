---
title: "Confusing change in installer"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by sander9860 on 2009-08-18
Back in the Gusty/Hardy days I tried installing Kubuntu on an external hard drive for the first time and I ended up messing up my MBR.  I then found an option on step 6 of 6 on installation where you click advanced and uncheck install bootloader, after which I used Neosmart's easyBCD to manually write the boot entry into windows vista's installer.  (It came up with a Grub bootloader in between the vista one and loading kubuntu, but I don't mind and other than that it was fine.)  I have used that technique to install Kubuntu in a dual boot on my laptop's internal HDD as well, but I want to do a fresh install (migrating to 64-bit Jaunty).  However, unchecking the boot loader option seemed to produce an unbootable system (windows still fine), and it looks like there are options in the box below are listed with sda, sda1, sda2, etc.  If I want NO CHANGE in my MBR or vista bootloader or anything like that, can I just tell it to write it to sda2 or whichever it actually is (I'll check first) or do I have to do something else?  I'm sorry if I just said the answer but I want to be sure as I don't have a lot of time for system troubleshooting as I go back to school in a couple days.  Thank you and I hope that wasn't too long.  If you need more info I'll get back pretty quick probably.

---

### Post by LowSky on 2009-08-18
you can write it anywhere you like, but keep in mind the partition location for that file for the MBR.

---

### Post by sander9860 on 2009-08-18
I can pick up the boot loader on the drive no problem (I think), I just need to know if this will affect my MBR.  Does it just write it into the MBR if I select sda, but just put it on the disk if I say sda2?

---

### Post by Bartender on 2009-08-18
Yes, if you go into the advanced box and tell it to install GRUB to the external drive, the installer will leave the Windows MBR alone.  Just make sure you are sending it to the right place.  
  
It doesn't help any that GRUB uses different nomenclature than Linux (hd0, hd1, etc.)

If you tell the installer to NOT install the bootloader, then your new Linux install will be missing a bootloader and it won't know how to start.  I didn't know you could tell it not to install at all!

---

### Post by presence1960 on 2009-08-18
in the advanced tab the choices are ( if you have that many disks)
sda = MBR of sda
sda1 = first sector of sda1 partition
sda2 = first sector of sda2 partition

sdb = MBR of sdb
sdb1 = first sector of sdb1 partition
sdb2 = first sector of sdb2 partition

sdc = MBR of sdc
sdc1 = I think you see what I mean

if you choose to install GRUB to partitions that is useful for chainloading off of GRUB on MBR when you have multiple linux distros or Easy BCD

---

### Post by sander9860 on 2009-08-21
Alright thanks guys I'm back up.

---

