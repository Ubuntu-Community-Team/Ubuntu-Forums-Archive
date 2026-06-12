---
title: "Cannot boot Ubuntu disk w Vista on another disk"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Goover on 2009-06-18
Well, You see the problem in the thread title - This is what I did:

To install Ubunto Desktop 9.04 I took away all 3 other disks from the Promise SATA 300 TX4 card using the SATA port #4.

Did several attempts to install but had quite a bit of problems that I eventually fixed, although I sometimes used GParted_Live CD to format in my attempts. So there were some manual attempts to install EXT4. However I did a complete install using the default from the Ubuntu Desktop ISO CD. I spent more than 30 hours of work to install lots of applications and server apps (Being a novice, I didn't want the server version, I wanted the windowing system).

I shrinked the Ubuntu partition to  ~495GB (Actually 460GB) and put on a 50 GB NTFS partition called X-changer. After that partition there is a 310.01 unallocated partition, before the ending 5.75 GB linux-swap. 

Now, I put back the other 3 hdd in the same order as I had them before. Vista on #1, and two NTFS formatted data drives on #2 and #3 - keeping the new 500GB drive, with Ubuntu as #4.

Reboot and no dual boot, even though BIOS is set up correctly on my "old" ABIT IC7 motherboard.

Steps:
1-----Computer only boots Vista
2-----Takes away Vista drive, #1. Reboots: NO BOOT DRIVE
3-----Takes away #2 and #3 and Ubunto boots.

Use: sudo fdisk -l
and got the following:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+  83  Linux
/dev/sda2           60051       60801     6032407+   5  Extended
/dev/sda3           13055       19581    52428127+   7  HPFS/NTFS
/dev/sda5           60051       60801     6032376   82  Linux swap / Solaris

GRUB 1.5 loads if I only have the UBUNTU disk in the system, and Ubuntu is loaded correctly.

Now, my question is: What can I do to make the system recognize both operating systems?

(If there is a way to save my Ubuntu installation, like making an image, and put it on back, moving partitions around et c, I'd be happy to do that.)

Thanks in advance for any suggestions that do't make all my work obsolete!

Goover

---

### Post by -kg- on 2009-06-18
One of your problems is that you did your Ubuntu install with your other disks disconnected.  When Ubuntu installs GRUB, one of the things that the GRUB installer does is search for other bootable OSes installed on the hard drive(s).  If the hard drives are not connected, the installer cannot include those OSes in the GRUB menu.

Your second problem is that, when you have your drives set up, it is checking the hard drive with Vista installed for the MBR (Master Boot Record).  Normally, when installing Ubuntu with another OS installed, the GRUB installer will install the GRUB bootloader into the MBR of the first drive.  Since you had that (and the other hard drive) disconnected, it installed GRUB in the MBR of the only disk you had available; your Ubuntu drive.

What you're going to need to do is reinstall GRUB in the MBR area of your primary (first) hard drive...the one with Vista on it.  First, go to the following thread and read it:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck]("http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck")

This will show you how to reinstall GRUB.  As I said, you will want to put it in the MBR area of your primary hard drive; the one with Vista on it, in your case.  Leave all your hard drives hooked up when you do this.  The GRUB installer should detect all of your OSes on your drives and install GRUB with these selections in the menu.

That should get you going, and if you have any further problems, feel free to post and we can give you further help.

:D

---

### Post by Goover on 2009-06-19
Thank you -kg- !

I will follow the instructions in the link!

(Why did I do it the way I did it - taking out the Vista drives?: Just wanted to be certain I did not destroy something, being a novice at Ubuntu).

Cheers,

Goover

---

### Post by Goover on 2009-06-19
Well, ...

I entered the commands as stated in the link.

However, that reversed the situation, now grub is in the MBR, but ONLY Ubuntu is started, and using ESC to be able to choose systtem to boot, there are three choices, BUT NOT VISTA.

So, now GRUB only boots the 4th drive. (I set the: root (hd3,0) and then setup (hd0))

QUESTION: How can I add Vista to the existing GRUB?

Thanks in advance!

Goover

---

### Post by Goover on 2009-06-19
I did find a way, I made a Super Grub bootable CD and now I can live swap to Vista, will fix the MBR to include Vista later on as I studied the included help info.

I consider this problem solved.

---

### Post by TJCIB on 2009-06-19
you need to at Vista to the menu.lst (i'll use graphical editor just in case you are more comfortable with that)

```
gksudo gedit /boot/grub/menu.lst
```

find the section that looks like this (it may be a little different depending on your specific configuration). You might also have more than two entries if you have multiple kernels installed:
```
title Ubuntu gutsy, kernel 2.6.22-12-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-12-generic root=UUID=17508b0e-6d71-4935-92d7-55ecbd47c183 ro quiet splash
initrd /boot/initrd.img-2.6.22-12-generic
quiet

title Ubuntu gutsy, kernel 2.6.22-12-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-12-generic root=UUID=17508b0e-6d71-4935-92d7-55ecbd47c183 ro single
initrd /boot/initrd.img-2.6.22-12-generic
```

You need to add Vista to the end of all these sections. So after your last Ubuntu entry paste this in:

```
title Windows Vista
root (hd0,0)
makeactive
chainloader +1
```

This assumes that Vista is on the first partition of your first hard drive (hd0,0)...if it is on a different hard drive or partition, you will need to change that accordingly.

Save, close, reboot

---

### Post by Goover on 2009-06-19
Thanks TJCIB,

I did as you suggested and then went back to the link -kg- gave me - using find and root and setup.

After that all works VERY NICE INDEED!

Thanks to both of you!

---

