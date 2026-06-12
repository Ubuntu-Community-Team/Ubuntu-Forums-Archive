---
title: "How do i dual boot vista and ubuntu on 2 seperate HDDs?"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by samn122 on 2010-08-25
I have Vista installed a 500 gb and recently added a 320 gb hard drive. How do I install ubuntu on to the 320 gb HDD and be able to dual boot the 2 operating systems? Also how do I keep myself from getting the  **symbol** 'grub_puts' **not found **error when updating to 10.4?

---

### Post by Jerry N on 2010-08-25
My way:  Temporarily disable the drive with Vista.  Install Ubuntu (or multiple linux OSs) on the new drive.  Reconnect the drive with Vista.  Tell the BIOS which drive to boot first.  If you want to boot the other one, during computer startup hit the key (or key combination) that will allow you to select which drive to boot from.  In the case of my Gigabyte MBs, it is the F12 key.  After you have booted to Ubuntu with the Vista drive in place, you _might_ find that Vista has been added to the Ubuntu list of boot options.

Jerry

---

### Post by -kg- on 2010-08-25
I'm going to assume that your Vista hard drive is the Master (sda) drive and your new hard drive will be the slave (sdb).  You can determine this by booting to the Ubuntu Live CD desktop and launching "System/Administration/Gparted" with the new hard drive connected.  Read the information at the link in my signature block and you will see what you're looking at.

Hopefully, the drive with the NTFS partition(s) will be sda and the new hard drive (hopefully with no partitions) will be sdb.  Which hard drive you're looking at can be determined by the drop-down box at the top right, as in the attached image below.

[ATTACH]167524[/ATTACH]

The hard drive being viewed in that image is my "/dev/sdc" drive; yours (being that the drive is new) should look similar and read "/dev/sdb".  When you first launch it, GParted should be showing your sda drive.  That drive should have at least one (and possibly two or more) partitions, and you should be able to determine that those partitions are NTFS (except sometimes for the Recovery partition).  They should also have a certain amount of "data" in them, depending on how full your Vista partition is.

When you pull down the drop box menu (click on the little arrows), you will have a selection for your other drive, which should be sdb.  When you select that, you should either have a drive exactly like the one in the image below, or there might be a partition on it, if it isn't ***brand* new.**  You need to be absolutely sure which is which, which shouldn't be too hard considering the two hard drives aren't the same size.

If your 500 GB hard drive (with Vista) is sda and your 320 GB hard drive is sdb (and has no partitions already on it), you should be able to do a normal install with no problems (this is also assuming that you want to use GRUB as your bootloader...if you're going to use something like EasyBSD there are special considerations, of course).

Make sure the installer is pointed at sdb in the partitioning section in whatever partitioning option you want to use.  This is especially important using the "Use Entire Disk" option.  This option will erase any and all partitions (and the information contained in them) before creating its partitions to install in.

Now if you want to boot autonomously (i.e., change the boot sequence in BIOS each time), just unplug your Vista hard drive before installation.  This will force the installation to your new hard drive and install GRUB in its MBR.  It preserves the Vista Bootloader in the MBR of your Vista Drive and installs GRUB in the MBR of the other.  The only thing you have to do when you want to boot the other OS is pop into BIOS and change the boot order or, like my laptop, press the appropriate "F" key and select the boot device.

There is also a method where you can force GRUB installation on to the 2nd drive without unplugging your Vista drive.  You just have to be sure to do it.  At the very last Window in the installer, you have a list of what actions are about to be performed.  There is a button on this Window that is labeled, "Advanced".  That button will allow you to determine where the installer installs the GRUB bootloader.  Make sure to set that at "sdb" (or whatever the drive designation of your target drive is).

I tend to over-explain. :p  What I'm really trying to tell you is that there are a number of ways to install Ubuntu, depending on how you want to handle it.  Tell us exactly how you want to do it, and we can walk you through that method.

My way is to let GRUB handle the whole thing and just do a normal install, making sure to point the installer to the correct drive and allowing GRUB to be installed in the MBR of the Vista drive.  It will detect Vista as well as Ubuntu and allow you to boot into either.

Also tell us if you want to have separate "/" (root) and "/home" partitions (I do, but I'm somewhat ambivalent about the necessity).  You will have to select "Manual partitioning" in the partitioning step, as this is not default.

<Edit> 
> Also how do I keep myself from getting the symbol 'grub_puts' not found error when updating to 10.4?

Where and under what circumstances did you get that message?  Are you talking about updating 10.04, or upgrading to 10.04?  If upgrading to, I would suggest a fresh install of 10.04 in the first place, since you're doing a new install anyway.

Of course, upgrading to 10.04 from a fresh 9.10 (or 8.04, if you're doing the LTS to LTS upgrade) shouldn't be a problem, anyway, but I'd recommend downloading the 10.04 .iso and just doing it totally fresh.

If it's updating 10.04, you shouldn't have any such problem, except under exceptional circumstances.

---

### Post by samn122 on 2010-08-26
Thanks for the reply. I was able to install ubuntu 9.10 on to the 320 gb drive and was able to use GRUB to select between the 2 operating systems with your help. The problem with the symbol 'grub_puts' not found error is that when im updating (i think its called updating because i use the update program) i get a error when i restart my computer. It wouldn't go to the screen where I can select the operating systems instead showed the "symbol 'grub_puts' not found" and *grub*-*rescue*>so i can't go into any OS except from booting from the live cd. I think its an error from updating because I don't know what options to select.

---

### Post by samn122 on 2010-08-26
Im still using 9.10, since I'm scared of screwing my entire system from updating like I did before. I had to do a clean intall of ubuntu 9.1 on the 320 gb to get GRUB working again

---

