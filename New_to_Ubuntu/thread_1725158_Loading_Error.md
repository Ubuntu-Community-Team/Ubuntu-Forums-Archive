---
title: "Loading Error"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by fantab on 2011-04-09
I have installed Ubuntu on my EXTERNAL HARD DISK, however when I restarted my desktop I got a Black Screen and on the top was displayed "**Error Loading Operation System**".

I use Ethernet Cable to connect to Internet however Ubuntu did not find it connected and during install I did not chose the option to "Download updates during installation".

I have set in my desktop board BIOS to boot from my External Hard Disk first, and have also enabled booting from USB Devices.

I have no problems with loading Windows (which means that I have installed my ubuntu and particularly GRUB at the right place).

I used 100GB of my EXT.Hard Disk space to install Ubuntu. From the alloted 100GB I created 3 partitions (Ext4): 20GB Primary(mount Point "/") -78GB Logical (mount point "/home")- 2GB Logical (Swap area).

What do you think I have done incorrectly?

---

### Post by Mr Stoozer on 2011-04-09
I don't think you've installed GRUB correctly. Where did you install it? 

If you installed GRUB to the MBR of your first hdd, (presumably where Windows is installed), you'll have the option of booting into either OS; whether the Ext HDD is plugged in or not. Is this the case or did you install it to the Ext HDD?

---

### Post by fantab on 2011-04-09
> **Mr Stoozer said:**
> I don't think you've installed GRUB correctly. Where did you install it? 
 
If you installed GRUB to the MBR of your first hdd, (presumably where Windows is installed), you'll have the option of booting into either OS; whether the Ext HDD is plugged in or not. Is this the case or did you install it to the Ext HDD?
 
I installed it on my Ext HDD. 
I wanted it on my Ext.HDD because when it is not plugged in I want windows to boot normally, but when Ext.HDD is plugged in Ubuntu should Load.

---

### Post by fantab on 2011-04-09
Eureka! I figured it out.
 
It was the problem with GRUB Installation. I was wrongly installing it on **sdb1** (where I have my Ubuntu installed). Then I tried installing GRUB on **sdb** and ho...ho...:D it works like a charm. When I plug in my Ext.HDD my computer loads Ubuntu and when it is not, Windows.

---

