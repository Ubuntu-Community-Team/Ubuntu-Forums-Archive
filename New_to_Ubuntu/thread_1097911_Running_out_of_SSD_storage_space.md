---
title: "Running out of SSD storage space"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by sanjio on 2009-03-16
I have successfully installed Ubuntu 8.10 on my ASUS EeePC 701 4G.  I made all the tweakes to get everything going including the wireless card.  My problem now is how can I get the system to save to the SD card and stop saving updates ect to the SSD?  

I also understand that I can save this copy of Ubuntu to a USB drive so that I can use it again with all the tweakes on another EeePC just like mine.

All suggestions will be greatly appreciated and I would be happyto share anything I have been able to do.  Sanjio

---

### Post by SuperSonic4 on 2009-03-16
If you were to install ubuntu with / mounted on the SD card it should install there by default. You may be able to copy and paste / onto the card but I don't know if it'd work or not. I doubt grub would.

For your own pc you may be able to edit your fstab making the SD card root but it'd be easier to reinstall onto the card imo.

[info on fstab]("http://wiki.archlinux.org/index.php/Fstab")

---

### Post by mister_pink on 2009-03-16
Use the disk usage analyser in accessories to see whats taking up the most space. You could then set it up so that one directory is mounted from the sd card.

---

### Post by mips on 2009-03-17
Are you clearing out your apt cache?

---

### Post by sgosnell on 2009-03-17
Save all your data to an SD card.  If you want, you can install the OS to an SD card, and not even use your SSD.  You can get a fairly large SD card pretty cheap if you look around on the internet tubes.  I have a 16GB card, and I've installed several distros on it, and it works very well on both my 701 and 900.  If you want to keep the OS on the SSD, then I would suggest linking /home to the SD card, and saving all data there.  As suggested, cleaning out the apt cache may restore some space.

---

