---
title: "Cleanup kernels with something other than synaptic"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by marco_polo99 on 2010-11-28
I've got a relatively new Asus 1015PE netbook that came with Windows 7 and a hidden Vista partition.  I initially set up to dual boot with the Ubuntu netbook version 2.6.32-25, but didn't like the netbook version so I installed the normal version 2.6.35-22.  When I went to boot into Windows  it corrupted the boot loader and it seemed my only recourse was to load another version of Ubuntu on the machine which did get things working again, but now with extra versions of Ubuntu.  I didn't have time to mess with the problem as I was off for a month trip to Haiti (which was why I bought the machine in the first place).  Eventually I tried to go back to windows again and not only would windows not load, but it again messed with the boot loader and I had to load yet another version of Ubuntu to get my loader menu working again.

I've finally punted on ever booting into Windows again (Windows7 stopped even showing up as a choice) and I'm ready to wipe it, but now I need to do a major cleanup.  I've got like 20 partitions on my drive from all the Ubuntu installs and many of the installs don't even work.  I've tried to clean up via synaptic,but it doesn't see all the versions for some reason (it doesn't see the netbook version), and I also have the same version multiple times on multiple partitions and don't want to remove them all, just redundant ones.  Since the synaptic route doesn't seem to be an option, can I go in and just wipe out the partitions that are redundant or that I don't want using something like gparted?  

Same for the Windows partitions?  

Here are my boot choices:
Ubuntu, with Linux 2.6.35-23-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+ serial console 115200)
Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda10)
Ubuntu, with Linux 2.6.32-25-generic (recovery mode on /dev/sda10)
Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda10)
Ubuntu, with Linux 2.6.32-21-generic (recovery mode on /dev/sda10)
Ubuntu 10.04 LTS (10.04) (on /dev/sda13)
Windows Vista (loader) (on /dev/sda3)
Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)
Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)
Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda8)
Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda8)

There seems to be an inherent incompatibility with the dual boot either tied to that machine or the newer version of Ubuntu.  I've dual booted with an older laptop for 3 years without these issues and don't think that I did anything different...  Help?

---

### Post by lidex on 2010-11-28
You could probably do it with a LiveCD, but I would go here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
to get and burn gparted to disk. Boot into that and you can wipe whatever you need from the computer hard drive. I would back up anything needed first. If you want to have a dual-boot with windows you should install it first, linux second. If you follow the correct procedures it will work.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by marco_polo99 on 2010-11-28
At this point I could care less about Windows--I don't have a CD to restore the corrupted version anyway and I'm not going to pay for a second copy just to reinstall it for the occasional use.

If I wipe out the partitions with distros that I don't want will grub recognize this and provide me with a valid boot list at the next startup or will all the ghost versions still be listed?  I want to keep at least one of the versions that I actively use (as opposed to wiping the whole drive and starting from zero).--If possible.

---

### Post by brianC on 2010-11-28
Would Ubuntu Tweak work? It has a cleanup

---

### Post by lidex on 2010-11-30
> **brianC said:**
> Would Ubuntu Tweak work? It has a cleanup

That just removes kernels, not installs/partitions.To the OP: I would seriously consider wiping the entire drive and installing from scratch.

---

