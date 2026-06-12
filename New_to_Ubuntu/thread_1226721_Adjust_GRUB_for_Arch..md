---
title: "Adjust GRUB for Arch."
date: 2009-07-29
forum: New to Ubuntu
---

### Post by BslBryan on 2009-07-29
Very noob question, guys, and I'm sorry.  This is what's going on.

I recently installed Arch in the following way:
```
/dev/sda5  Boot  100MB
/dev/sda6  Swap  1000MB
/dev/sda7  Root  20GB
/dev/sda8  Home  25GB
```
Similar stories found all over Google, I want to edit my existing GRUB to boot Arch and Ubuntu.  

After editing /boot/grub/menu.lst 4 or 5 times, I've realized that I must be missing something big, considering I keep getting different errors.  Here's my /boot/grub/menu.lst:

```
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=dcc25d25-67a3-478e-8e74-00e288ccf554 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic


title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=dcc25d25-67a3-478e-8e74-00e288ccf554 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin


### END DEBIAN AUTOMAGIC KERNELS LIST

title        Arch Linux
root        (hd0,2)
kernel        /boot/vmlinux26 root=/dev/sda5 ro
initrd        /boot/kernel26.img

title          Arch Linux Fallback
root           (hd0,2)
kernel        /boot/vmlinuz26 root=/dev/sda5 ro
initrd        /boot/kernel26-fallback.img
```

Again, I apologise.

Thanks!

---

### Post by Ji Ruo on 2009-07-29
Your Arch /boot is in sda5 but you've told GRUB to look for it (root) in (hd0,2). Shouldn't it be (hd0,4) ? Give that a try.

---

### Post by BslBryan on 2009-07-29
Thanks a lot, but I still get an Error 15: File not found.

---

### Post by Ji Ruo on 2009-07-30
I have managed to get GRUB to load a few different distros on my computer, but you've installed Arch across several partitions which is a bit new to me. You may have to wait for someone more experienced to get an answer!

If you're willing to experiment, the next thing I would try is changing the root argument in your arch kernel line to ```
/boot/vmlinux26 root=/dev/sda7 ro
```Presumably this line is to tell the kernel where your root is located, and you've put it in the sda7 partition.

---

### Post by BslBryan on 2009-07-30
Thanks, mate, but I still get the error 15.  

I've done a find /boot/grub/stage1 and it's output was (hd0,0), so I adjusted menu.lst accordingly.  Still no luck.

---

### Post by BslBryan on 2009-07-30
Bump.

---

### Post by BslBryan on 2009-07-30
Bump.

---

### Post by bodhi.zazen on 2009-07-30
See if this helps : 

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

also your arch root partition is /dev/sda7 , not /sda5

---

### Post by Ji Ruo on 2009-07-31
There's some advice on [this page]("http://http://wiki.archlinux.org/index.php/Beginners_Guide"), let me take you through it (assuming you are still stuck).

First of all, it recommends you specify your root partition to the kernel by UUID. Go into a terminal and```
blkid
```This will list all of your partitions by their UUID. Your root partition is in sda7, so this is the one you want to make a note of.

I think it would be a good idea to check the name of the kernel and initrd in your  boot partition (sda5) as well, to make sure that they are named as you have them now (vmlinuz26 and kernel26.img). Go into Nautilus and check the partitions listed until you find the one that has these names. If you find something different you should use those names instead (you probably won't, but it doesn't hurt to check).

Your root value for GRUB should be the boot partition which is sda5 (first hard drive, 5th partition). Translated into GRUBese this is (hd0,4) as GRUB counts hard drives and partitions from 0. The guide also states that you shouldn't have the </boot> in front of the kernel and initrd, so we'll leave those out.

Edit the Arch listing in menu.lst to this -```
title        Arch Linux
root        (hd0,4)
kernel        /vmlinux26 root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxx ro
initrd        /kernel26.img
```adjusting for whatever you've found above as necessary.

Cross your fingers for luck and give that a try. If it doesn't work, I would recommend double checking the UUID or anything else you've altered. Post back if you still can't get it to work, but you might want to try the [Arch Forums]("http://bbs.archlinux.org/") from there.

If it does work, the root and kernel lines for your fallback entry will be the same, and just take the /boot off the initrd line.

---

### Post by kpkeerthi on 2009-07-31
I prefer [GRUB chainloading]("http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html")

---

### Post by bodhi.zazen on 2009-07-31
> **kpkeerthi said:**
> I prefer [GRUB chainloading]("http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html")

Try configfile

---

