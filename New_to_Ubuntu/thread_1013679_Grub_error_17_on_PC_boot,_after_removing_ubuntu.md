---
title: "Grub error 17 on PC boot, after removing ubuntu"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by derisen on 2008-12-17
(am only a started to linux)

My PC was installed with Ubuntu and windows XP and windows 2000.

I didn't has any problem on ubuntu installation. Since my dial-up-modem wasnt automatically detected in the OS insalltion, I tried the workaround got from the this forum(which worked in my earlier installation). And it wasn't successfull and on the subceding boot process to ubuntu, a scanning process had happened automatically. In the scan, it has detected that some filesytem is not able to read and has to manually do the fsck. After doing so, it didnt help to load the os. So from the live CD, I used the partition editor and deleted the 'linux swap', '/boot' and '/' and formated the combined partition with Fat32. When I restared after the entire tasks, an error:
Grub Loading... 
Error 17
is displaying in the black screen.

Because of this, now am not able to enter other OS's. So wasn't able to get into internet for browsing also. Now am posting this from another PC.

Please help me to solve this issue....

---

### Post by Elfy on 2008-12-17
You should have reinstalled the windows bootloader before you removed ubuntu - boot with one of your windows discs and you can use it to fixmbr

When it boots it will ask if you want the recovery/repair option - yes 

Once you get to the prompt you can use fixmbr to repair it

Edit - if you don't have either of the discs you can use supergrub - download it, burn as an iso and boot with it, there's a fix win option.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

