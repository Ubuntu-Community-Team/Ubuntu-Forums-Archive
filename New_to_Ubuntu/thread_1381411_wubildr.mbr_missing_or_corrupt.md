---
title: "wubildr.mbr missing or corrupt"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by pwnzerfaust on 2010-01-14
Hello all,

I am totally new to Linux and Ubuntu, but wanted to try it out. Unfortunately I haven't even made it in the front door yet =(

I used wubi to download and install Ubuntu. Everything seems to have gone just fine, but when I get to the boot menu where you choose which OS to run, I get the error message "wubildr.mbr" is missing / corrupt and the system can't proceed. Then I boot into Vista and wail like a n00b on some forums.


all the files seem to be where they should be, including wubildr.mbr/ However, I installed ubuntu on a totally separate hard drive with nothing else installed - it had just been formatted. So my first question:

Can I install Ubuntu on an actual separate, empty hard drive (NTFS) rather than a partition of an existing, vista-using drive?

Other things that I think might affect booting into Ubuntu:
1) My main hard drive is a SATA drive, the one with Ubuntu on it is IDE
2) This IDE drive is sharing a single IDE port with my DVD burner
3) I left the jumpers on the DVD and HDD to "cable select" and the hard drive ended up the slave

I can put data on the ol' IDE drive, and in fact I can see the Ubuntu files on it, just where they should be. So my second question:

How do I figure out if the computer is looking for wubildr.mbr in the right place on boot?

I have, in fact, tried to find this problem in previous posts and haven't found anything yet. If a standard solution exists, I'd be happy if someone could just link to it.

Please keep in mind that I really have not done much tinkering with the software side of Windows, and none at all with Ubuntu...

Thanks!

---

### Post by sandyd on 2010-01-14
> **pwnzerfaust said:**
> Hello all,

I am totally new to Linux and Ubuntu, but wanted to try it out. Unfortunately I haven't even made it in the front door yet =(

I used wubi to download and install Ubuntu. Everything seems to have gone just fine, but when I get to the boot menu where you choose which OS to run, I get the error message "wubildr.mbr" is missing / corrupt and the system can't proceed. Then I boot into Vista and wail like a n00b on some forums.


all the files seem to be where they should be, including wubildr.mbr/ However, I installed ubuntu on a totally separate hard drive with nothing else installed - it had just been formatted. So my first question:

Can I install Ubuntu on an actual separate, empty hard drive (NTFS) rather than a partition of an existing, vista-using drive?

Other things that I think might affect booting into Ubuntu:
1) My main hard drive is a SATA drive, the one with Ubuntu on it is IDE
2) This IDE drive is sharing a single IDE port with my DVD burner
3) I left the jumpers on the DVD and HDD to "cable select" and the hard drive ended up the slave

I can put data on the ol' IDE drive, and in fact I can see the Ubuntu files on it, just where they should be. So my second question:

How do I figure out if the computer is looking for wubildr.mbr in the right place on boot?

I have, in fact, tried to find this problem in previous posts and haven't found anything yet. If a standard solution exists, I'd be happy if someone could just link to it.

Please keep in mind that I really have not done much tinkering with the software side of Windows, and none at all with Ubuntu...

Thanks!
thats a common problem nowadays....

just do this.

delete the empty ntfs partition.
leave it as free space.

boot up the ubuntu cd, choose install.

when you get to the partitioning stage, choose "use largesg contineous block of free space"

---

### Post by pwnzerfaust on 2010-01-14
Thanks for the quick reply!

I was hoping to stick with the GUI installer as I have not bothered to hunt down CD/DVD burning software in some time.

Before I go off and try to find some freeware, I'd like to make sure we are speaking the same language: 

I'm definitely NOT installing on a partition of a currently used drive. I would be installing on a formatted but empty hard drive that is physically separate from the one that has winblows on it.

Is this OK?

sorry to be nitpicky, I am an engineer by trade and have tenous communication skills - I like to avoid confusion if at all possible.

Thanks again!

---

### Post by Argosse on 2011-01-01
Im very new also but I think you can install thru wubi on windows onto your empty drive, then for precautions I would copy the wubildr.mbr from your original drive onto the drive you install at the lowest lvl you can say /etc/wubi/wubildr.mbr. Then use this link I found 
[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)  and from there figure out how to use whichever bootloader you want ie GRUB2 from linux or the windows boot. Im not sure of that part.  



Im currently looking at a wubi install from windows xp on my C:/ drive and Ubuntu was install to my J:/ HDD, my C drive fails to read anything and now I need to figure out how to rebuild a copy of the wubildr.mbr onto my ubuntu drive J which is just missing any boot entry to tell the pc to look into my wubi folder for linux

---

