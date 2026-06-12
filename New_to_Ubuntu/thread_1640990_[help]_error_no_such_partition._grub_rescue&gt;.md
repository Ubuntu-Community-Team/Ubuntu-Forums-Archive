---
title: "[help] error: no such partition. grub rescue&gt;"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by whatislove on 2010-12-08
Hey guys!
Well a few fomths ago finally decided to fix my old computer that had a broken version of vista installed. It would boot and all my files were there, but it just would not connect to the internet. I figured why not linux, since my phone runs on android it should be simple to understand. I installed ubuntu 32-bit on my computer and it worked alright. This was not my main computer, so I left it to my little sisters to play and do everything they wanted. Eventually, there were over 100 critical updates to install, firefox decided it didn't want to launch anymore, and flash was going wayyyy too slow. I decided to just delete the entire partition and install a fresh copy of ubuntu 10.10 64-bit (since there is 64-bit flash now). I booted into windows and deleted the partitions using windows disk manager. When I rebooted the computer to install from the livecd I burned earlier, and to my surprise I ended up with this:
```
error: no such partition. 
grub rescue>
```No commands that I throw at it are recognized. I can't boot from the cd or boot from the hard drive. I do have access to the bios screen. though. I don't have the windows recovery disks nor do I have access to my recovery partition. What would be the simplest way of getting my computer back to a working state? 

Thanks in advance guys.

PS: the specs for my computer are AMD 8400 3 core processor, 4 gigs ram, vista home premium (factory installation), and NVIDA 6450 graphics card

---

### Post by oldfred on 2010-12-08
The part of grub in the MBR just loads the rest of grub in the Ubuntu partition. If you delete the partition, grub has nowhere to go. 

If you are reinstalling Ubuntu, just use liveCD or USB flash drive and do that. Grub in the MBR will get overwritten.

If you want windows back you have to install a windows boot loader. You can/should have a windows repair CD for the version of windows anyway. You can also install a generic windows style boot loader from Ubuntu (or most Linux rescue CDs). You also should have Ubuntu liveCD and/or a rescue type CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

