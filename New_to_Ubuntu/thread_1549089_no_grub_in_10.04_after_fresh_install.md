---
title: "no grub in 10.04 after fresh install"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by trinidadflores on 2010-08-09
i just did a fresh install of 10.04 and now i cannot boot in to either windows or ubuntu without using a live disc.  how can i fix this?

---

### Post by corrytonapple on 2010-08-09
If there is no grub, do you see anything else? How about hitting shift to get the grub menu.

---

### Post by trinidadflores on 2010-08-09
the following image is what i see when i boot now.  The only way i can get around this is if i reboot with the live disc in,  please see the attached picture.

---

### Post by corrytonapple on 2010-08-09
See this:
[http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html](http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html)
Or if that does not work try this:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by elliotn on 2010-08-09
Just reinstall again, it worked for me before

---

### Post by corrytonapple on 2010-08-09
> **elliotn said:**
> Just reinstall again, it worked for me before
Are you suggesting reinstalling the OS or or reinstalling GRUB?

---

### Post by elliotn on 2010-08-09
I reinstalled the whole Os

---

### Post by corrytonapple on 2010-08-09
Reinstalling could just bring back up the issue. If GRUB was corrupted, then the disc could be bad. Reinstalling GRUB is easier than a whole OS.

---

### Post by trinidadflores on 2010-08-09
I have tried to reinstall the os several times already and nothing. but i am going to try it again.  I will be back on after the reboot.

---

### Post by trinidadflores on 2010-08-09
I have tried to update it off of 9.10 also and still have the same issue.  Also I have used 4 different copies of 10.04 and each one has the same issue too.

---

### Post by john newbuntu on 2010-08-09
Yeah, I would suggest fixing grub rather than re-installing.  As corrytonapple pointed out in this link earlier, follow step 15 in that link and it should help.  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Should you get stuck or confused, boot using your liveCD, open up a terminal (Applications->accessories->terminal), run the command and post the output of:
```
sudo fdisk -lu
```

---

### Post by trinidadflores on 2010-08-09
> **john newbuntu said:**
> 
```
sudo fdisk -lu
```

here is the output of the above code

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a879

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   275627204   137813571    7  HPFS/NTFS
/dev/sda2       275627205   283531184     3951990    7  HPFS/NTFS
/dev/sda3       283531185   312576704    14522760    5  Extended
/dev/sda5       283531248   312576704    14522728+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0fc8e150

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   625139711   312568832    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by john newbuntu on 2010-08-09
When you get to the "grub rescue>" prompt that you showed in the picture, please enter the following commands one after the other.  Some may take a few seconds to run.  Should you encounter any problems, please write it down and post back:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
ls /boot/
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```Hopefully, this should boot you in.  As soon as you boot in, enter the folllowing commands:

```
sudo update-grub
sudo grub-install /dev/sda
```

---

### Post by trinidadflores on 2010-08-09
> **john newbuntu said:**
> When you get to the "grub rescue>" prompt that you showed in the picture, please enter the following commands one after the other.  Some may take a few seconds to run.  Should you encounter any problems, please write it down and post back:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
ls /boot/
insmod (hd0,5)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```Hopefully, this should boot you in.  As soon as you boot in, enter the folllowing commands:

```
sudo update-grub
sudo grub-install /dev/sda
```


I will give this a try and will report back and let you all know what happens

---

### Post by trinidadflores on 2010-08-09
after i imput the following lines i get a error that says "cannot get C/H/S Values"```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
ls /boot/

```

---

### Post by -kg- on 2010-08-09
> Device Boot Start End Blocks Id System
/dev/sda1 * 63 275627204 137813571 7 HPFS/NTFS
/dev/sda2 275627205 283531184 3951990 7 HPFS/NTFS
/dev/sda3 283531185 312576704 14522760 5 Extended
/dev/sda5 283531248 312576704 14522728+ 83 Linux

Device Boot Start End Blocks Id System
/dev/sdb1 * 2048 625139711 312568832 7 HPFS/NTFS

What method did you use to install?  I find it odd that you have no swap partition.

---

### Post by trinidadflores on 2010-08-09
> **-kg- said:**
> What method did you use to install?  I find it odd that you have no swap partition.

I never use a swap.  i have never had to in the past nor when i had 9.10 on here i never used it. so now just out of habit i dont set one up.

---

### Post by Elmer Fudd on 2010-08-09
> **trinidadflores said:**
> I never use a swap.  i have never had to in the past nor when i had 9.10 on here i never used it. so now just out of habit i dont set one up.

Did not realize that Ubuntu would run well (or at all) without a swap.

---

### Post by john newbuntu on 2010-08-10
There are a few things you could try when you get the "cannot get C/H/S Values" error:

1. Continue with the other commands I gave.

2.  If that does not work, instead of:
           insmod (hd0,5)/boot/grub/linux.mod
     try:
           insmod /boot/grub/linux.mod

3.  instead of: insmod (hd0,5)/boot/grub/linux.mod, try:
```
   insmod normal
   normal
```

4.  instead of: insmod (hd0,5)/boot/grub/linux.mod, try:
```
   insmod linux
   normal
```

5. Take a look at what oldfred suggests in this post(setting hard disk to auto in BIOS):
[http://ubuntuforums.org/showthread.php?t=1336849](http://ubuntuforums.org/showthread.php?t=1336849)

---

