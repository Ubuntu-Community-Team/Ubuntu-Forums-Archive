---
title: "Grub error 21"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by wanksta2010 on 2009-03-16
I've found some other posts on Grub error 21, but I didn't have any luck with any of the solutions offered.

Here's my situation: I wanted to try Ubuntu, but wanted to keep XP on my laptop.  I tried to install from the live CD and resize the XP partition, but it would not let me resize it.  Similar to this problem: [http://ubuntuforums.org/archive/index.php/t-279494.html](http://ubuntuforums.org/archive/index.php/t-279494.html)  I tried all of the solutions suggested there with no luck.

SO, I installed Ubuntu on an external USB hard drive.  It is up and running fine, and dual boots correctly when the USB drive is plugged in.  The trouble is, when the USB drive is not plugged in when I boot, it gives me Grub error 21 and won't boot XP.  Is there any way to fix this so it boots XP when the external drive is not plugged in?

---

### Post by lindsay7 on 2009-03-16
If your computer will start from the usb drive then you bios is set to start from that first. Everytime you start your computer it looks for the usb. You have to reset your bios to start from the hard drive first if you are not going to keep the usb plugged in.

---

### Post by meierfra. on 2009-03-16
To fix your problem, you need to install grub to the MBR of the  external drive and and repair the MBR of the internal drive.
Open a terminal in Ubuntu (Applications->Accessories->Terminal

**Step 1 Install Grub to the MBR of the external  drive.**


```
sudo grub 
```

and at the "grub>" prompt.



```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)

Still at the "grub>" prompt:


```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")


**Step 2) Install a Windows Style MBR to the internal drive:**

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
(Here "/dev/sda"  needs to be the device name of your internal drive. It probably is "/dev/sda" but you should double check via "sudo fdisk -lu")


Now reboot, but set your bios to boot from the External drive.

You still need to fix "menu.lst" so that you can boot into Windows from the Grub Menu. But we'll worry about that later.

---

### Post by bobmatino17 on 2009-03-16
i had the same error.
[http://ubuntuforums.org/showthread.php?t=1081550]("http://ubuntuforums.org/showthread.php?t=1081550") might help you.

---

### Post by wanksta2010 on 2009-03-17
Thanks for the reply.  At the grub prompt when I type find boot/grub/stage2 it says error 15: file not found.  Same happens when I try find boot/grub/stage1.

---

### Post by wanksta2010 on 2009-03-19
Just tried it again, and it worked!  I was probably doing something wrong before.  Thanks again.

---

### Post by meierfra. on 2009-03-19
> Thanks for the reply. At the grub prompt when I type find boot/grub/stage2 it says error 15: file not found. Same happens when I try find boot/grub/stage1.

Sorry, for the delay. I thought I already  had responded to this post, but seemingly I didn't.


> Just tried it again, and it worked

Glad you got it to work. Have fun with XP and Ubuntu.

---

