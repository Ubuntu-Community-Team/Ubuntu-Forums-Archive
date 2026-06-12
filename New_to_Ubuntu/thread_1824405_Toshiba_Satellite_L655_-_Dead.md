---
title: "Toshiba Satellite L655 - Dead?"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2011-08-13
Hello all.

I was trying to compile a custom kernel just about 3-5 hours ago and my computer ran into kernel panic (it usually does; flashing caps lock key). I'm on a toshiba satellite L655 and it is known to have problems with ubuntu (battery, wifi, and audio - fixed all of them some time ago). When it entered kernel panic, I was compiling the kernel using the latest release of the git branch of ubuntu-natty kernel (found on ubuntu's site). I started up ubuntu again and it said something along the lines of "GNOME power manager configuration didn't install correctly." (I don't remember exactly what it said) There was no background on the login screen, and whenever I tried to log in, it just kicked me back to the login screen. The screen was also themeless (I think that's the word - no colors and it looks like some crappy windoz 2000 screen)

When I booted into windoz, it said some software/hardware failure prevented it from booting, yet when I said to "boot normally", all seemed well. I'm currently on an ubuntu live image, so I can't really do anything right now. I ran ```
fdisk -l
``` and it did NOT say anything about "cannot read partition table", so the partition table isn't corrupted, AFAIK. Also, I'm using a WUBI install, so that COULD somehow explain how windoz kinda messed up, too.

I seriously need some help, as my school starts within a week.

Thanks in advance.

---

### Post by bcbc on 2011-08-13
I'm not really clear on what happened. You say that it's normal to have kernel panics? What kernel boot options are you using for the L655 if any?

The other thing is that compiling a kernel can take a lot of space - so is it possible that you ran out of space on the root.disk?

I would try mounting it from the live USB and check the size. e.g. if your root.disk is on /dev/sda2
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
df -h
```

Post the results back.

---

### Post by kroq-gar78 on 2011-08-14
K I'll post back when I have access to an ethernet cable (laptop's wifi not supported by default in my Ubuntu 10.10 live image).

It's normal to have kernel panics and stuff ONLY on my laptop (when I mean only I mean versus all of my 5 other ubuntu machines) and I think it said somewhere in the terminal output "firefox-bin tainted" (or something like that). I use default kernel options in GRUB and some option to resolve the overconsumption of power in 2.6.38 kernel (natty kernel). I had a lot of kernel panics even before that quick power consumption fix.

Also, it turns out that, if I boot into "recovery mode" in the WUBI grub, I CAN log in, so I'll try to remove some crap kernel sources I have.

Thanks for the help for now.

---

### Post by kroq-gar78 on 2011-08-15
*bump*

I REALLY need this fixed soon...
I just can't stand Windoz and its updates :| it took a day to do ONE uodate

---

### Post by LowSky on 2011-08-15
It's called Windows. How hard is it to write two more letters?

If you really wish to use Ubuntu, don't use WUBI do a real install of the entire hard drive or dual boot.

The reason for your kernel panics are probably a cause of the NTFS file system (Windows) possible fragmentation, or maybe a free space issue. The is no reason you should have constant panics.

I suggest you back up all data. Delete the WUBI partition from Windows, then do a normal Ubuntu dual boot installation.

---

### Post by kroq-gar78 on 2011-08-15
> **LowSky said:**
> It's called Windows. How hard is it to write two more letters?
Yeah sorry, I just wrote the "oz" because of muscle memory there. Didn't really care to fix it. Windows.

Ok, so about the constant kernel panics: The first few times I saw something about a "tainted firefox-bin" or something like that in the error message dump after the caps lock key starts flashing. This "tainted" stuff happened from firefox4 to the upgrade to firefox5, and I believe the problem still persists. And no, it's not an out of space issue (the kernel crashes) b/c it happened on my 1st week of using WUBI, when I still had 20-30GB of free space on the wubi. But the reason why everything got "corrupt" (not really sure if it IS corrupt, but it does kinda LOOK like that to me) might be the lack of disk space - I was compiling a new kernel and that might have taken up the only 2-4 free GB's of space on WUBI.

The only reason I was using a WUBI install is b/c I might have to (for whatever reason - say ubuntu somehow "stops working") remove Ubuntu. I read somewhere that if you want to remove Ubuntu on a windows (I fixed it this time :P) dual-boot install you have to do some tricky stuff with the MBR. Correct me on that if I'm wrong, because I barely know anything about grub, MBR, etc.

About the "backup all data" - how do I backup minesweeper scores? That's the only non-document stuff I really REALLY want (I finally got a sub-3 minute time on expert :D). You might not know it, so I'll explore where they might be located.

Also, how do you suggest I partition my computer? Should I have a /boot partition (and how big? 100-200MB?)? Should I put the ubuntu and swap partitions in an extended partition?

Sorry for the bombardment of questions, but thanks for helping.

P.S. How big of a partition of EXT4 (or ext3/2) do you recommend for Ubuntu? 50GB? I'll have all my home folders symlink'd to my Windows documents/files b/c I want them to be available on both, but Windows can't symlink - therefore I chose to symlink ubuntu to windows.

**UPDATE:** Turns out I was just out of space. I removed one of the old kernel sources and now I can boot into Ubuntu and go about regular business. Though, I still would like to see about that partitioning business. Can you help?

---

### Post by bcbc on 2011-08-15
> **LowSky said:**
> 
The reason for your kernel panics are probably a cause of the NTFS file system (Windows) possible fragmentation,... 
No. That's not plausible since if there is a problem on the ntfs system the virtual disk will not mount. More likely this will trigger a chkdsk on windows and the root.disk will be repaired or removed to a recovery directory \found.000. As I always say, there are enough valid reasons to switch from wubi (install fresh or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354")), without inventing new ones ;)

> **kroq-gar78 said:**
> might be the lack of disk space - I was compiling a new kernel and that might have taken up the only 2-4 free GB's of space on WUBI.


When I built a kernel it took about 8GB - I think there is an option to turn off debug mode that I missed (so maybe 8GB is high), but if you're trying to do this with only 2 GB it is definitely going to fail.

---

### Post by kroq-gar78 on 2011-08-16
> **bcbc said:**
> No. That's not plausible since if there is a problem on the ntfs system the virtual disk will not mount. More likely this will trigger a chkdsk on windows and the root.disk will be repaired or removed to a recovery directory \found.000. As I always say, there are enough valid reasons to switch from wubi (install fresh or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354")), without inventing new ones ;)



When I built a kernel it took about 8GB - I think there is an option to turn off debug mode that I missed (so maybe 8GB is high), but if you're trying to do this with only 2 GB it is definitely going to fail.
K thanks for the info.

I figured that 2GB won't be enough (took me a while :P), so I removed some old kernel source and it's up and running again.

I'm going to try your migration script. It looks like some pretty slick stuff!

I'll post back tomorrow (or tonight).

Thanks all!

---

### Post by kroq-gar78 on 2011-08-27
Sorry, I kinda forgot about this thread.

Well, now it all works fine! I still have a few kernel crashes/panics, but otherwise it's all fine.

I migrated by WUBI install to a ext4 partition, and it's WAAAY faster, too.
So, in the end, I just ran out of space.

Thanks all, I'm marking this thread as solved.

---

