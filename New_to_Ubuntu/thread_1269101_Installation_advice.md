---
title: "Installation advice"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by Woody3 on 2009-09-17
I have a 60g drive with a 30g partition with windows on it. I will be using a dule boot
but have 2 concerns. Right after instalation the system advises me to download updates but there is not enough space in the I partition. Can the I partition be resized so I don't have to learn to use that sudo app-set clean program right away! If I install a driver that locks the system up is there any way to do a system restor like in windows? Well I wiped the drive and now it only has that first partition with windows
on it so I wanted a little advice before I re installed ubunty.

---

### Post by overdrank on 2009-09-17
> **Woody3 said:**
> I have a 60g drive with a 30g partition with windows on it. I will be using a dule boot
but have 2 concerns. Right after instalation the system advises me to download updates but there is not enough space in the I partition. Can the I partition be resized so I don't have to learn to use that sudo app-set clean program right away! If I install a driver that locks the system up is there any way to do a system restor like in windows? Well I wiped the drive and now it only has that first partition with windows
on it so I wanted a little advice before I re installed ubunty.

Hi and welcome, you may use the live cd to resize your partition. 
Moved to Absolute Beginner Talk

---

### Post by ghostborg on 2009-09-17
Check out Wubi installer.
Installs Ubuntu in the Windows partition and gives you a choice upon booting which OS to run.
[http://wubi-installer.org/]("http://wubi-installer.org/")

To recover from a bad driver install
During Grub loading hit the ESC key to see your options and choose
the recovery option or a previous kernel if available.

Ubuntu bootable CD Live should have Gparted in the menu somewhere which will resize partitions. BE CAREFUL.

---

### Post by egalvan on 2009-09-17
Isn't there a bug which affects this kind of install?

It ends up making a tiny 2GB partition, regardless of the amount of empty drive space.

I can't recall the details...
can other recall?

---

### Post by seshomaru samma on 2009-09-18
you have a 60g drive with a 30g partition for windows?
assuming you dedicate the rest to ubuntu you will have something like 1g for swap and 29g for root (ubuntu).
29g should be enough even if you download the latest updates.

personally i would stay away from wubi , i like to give linux its own partition in a dual boot. if wubi breaks its difficult to use linux tools to fix it. 

i would also be careful with using the live cd to resize windows. personaly i would go with a windows tool like partition magic if you want to resize ntfs. some people recommend defraging before resizing

---

### Post by mapes12 on 2009-09-18
For all things dual boot: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

