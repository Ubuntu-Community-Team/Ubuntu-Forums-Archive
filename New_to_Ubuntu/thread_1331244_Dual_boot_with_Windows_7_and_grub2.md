---
title: "Dual boot with Windows 7 and grub2"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by rookworm on 2009-11-19
Hello,

I recently formatted my computer, installed Karmic, repartitioned and installed windows 7. Windows overwrote my boot sector, and in repartitioning, the swap went from the first to the fourth partition.

Just wondering how to get my system to give me a dual boot menu without overwriting my Karmic partition (already nicely set up). All the info I can find only applies to grub 1.......

I have a 9.10 live cd, and I don't know how to boot into the partition with Karmic.... If there is an automagical option for doing it, that would be really sweet.

Thanks!

---

### Post by whitethorn on 2009-11-19
A quick google search game me this.

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

and this

[http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html](http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html)

---

### Post by ukripper on 2009-11-19
> **rookworm said:**
> Hello,

I recently formatted my computer, installed Karmic, repartitioned and installed windows 7. Windows overwrote my boot sector, and in repartitioning, the swap went from the first to the fourth partition.

Just wondering how to get my system to give me a dual boot menu without overwriting my Karmic partition (already nicely set up). All the info I can find only applies to grub 1.......

I have a 9.10 live cd, and I don't know how to boot into the partition with Karmic.... If there is an automagical option for doing it, that would be really sweet.

Thanks!

Follow this guide to sort your  Grub2 after windows installtion - [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by rookworm on 2010-01-17
thanks, ukripper, I've used that last guide many times so far!

---

