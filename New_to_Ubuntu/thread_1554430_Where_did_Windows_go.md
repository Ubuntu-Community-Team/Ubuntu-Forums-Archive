---
title: "Where did Windows go?"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2010-08-16
I just got an SSD and I popped in the Windows 7 install CD, it made it all the way to the reboot and my system freaked out.

I've managed to restore grub to the point where I can get Ubuntu to boot on the HDD.

Basically, I want the HDD to have GRUB and give me the option to boot Ubuntu on the HDD or Windows on the SSD. The problem is, I don't know where this half of a Windows install is (other than the partitions on the SSD) and how to configure GRUB correctly.

What do I do?

---

### Post by Lazy-buntu on 2010-08-16
I tried something similar to this, but I'm not sure whether to use hd0 and hd1 or sd1. 

[http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives](http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives)

By the way I've got 3 SATA drives:

1 750GB HDD
1 640GB HDD
1 60GB  SSD

---

### Post by jtarin on 2010-08-16
The command in a terminal```
fdisk -l
``` will list all known partitions. Look for each partition by size and format to determine which are the ones your looking for.
[Some Grub info]("http://www.ibm.com/developerworks/linux/library/l-grub2/?ca=drs-").

---

### Post by Lazy-buntu on 2010-08-16
I tried adding the Grub lines:

```

#Windows 7 on SSD
title Windows 7 Pro (SSD)
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

fdisk gives:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         154       19122   152368492+   b  W95 FAT32
/dev/sda2           19123       32763   109564928    7  HPFS/NTFS
/dev/sda3           32764       80620   384411352+   7  HPFS/NTFS
/dev/sda4           80621       91201    84991882+   5  Extended
/dev/sda5           80621       90181    76798701   83  Linux
/dev/sda6           90182       91201     8193118+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026e09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15936   128000000    7  HPFS/NTFS
/dev/sdb2           15936       29576   109568000    7  HPFS/NTFS
/dev/sdb3           29576       77826   387560448    7  HPFS/NTFS

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x688ff19d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7458    59904000    7  HPFS/NTFS

```

You can see /dev/sdc1 is the SSD partition where Windows is trying to install. Ubuntu is on /dev/sda5

Everything on sdb is data.

---

### Post by Lazy-buntu on 2010-08-16
I'd like to stick with GRUB legacy if possible, but would installing Grub2 fix my issue?

---

### Post by jtarin on 2010-08-16
I've noticed you have three active* partitions......any reason for that?The SSD I can understand. The SSD will be read by the bios as having the lowest logical disk number....One(1).... and will be seen as drive C on boot no matter where you place it.This is why windows wants to install there. Might check with your bios mfg. and see if they have options to adjust for this behavior.

---

### Post by Lazy-buntu on 2010-08-18
Okay, so I finished installing Windows 7.

Now my issue is this: if I put the SSD as a higher boot priority Windows 7 boots.

If I put the HDD as a higher boot priority I can boot Ubuntu.

What I want to do is leave the HDD as the highest boot priority and have it point to the Windows boot loader on the SSD, so I can boot either Ubuntu or Windows from Grub.

I guess if I really have to I can flip flop that BIOS settings every time I want to boot Ubuntu, but it would become a pain fast. Any ideas of avoiding that? It seems like that would be he same idea as that link I posted earlier, but maybe I'm getting my labels mixed up. 

I've tried hd1, hd2, and sd2 in the Grub menu.lst lines to no avail.

---

### Post by oldos2er on 2010-08-18
Why aren't you using grub2?

---

### Post by oldfred on 2010-08-19
I agree that grub2 would be better. Its osprober is very good at finding other systems and letting you boot them. Old grub often had us creating a boot stanza and sometimes experimenting with drive number.

It may be hd1 or hd0, but normally grub2 makes the boot drive hd0 and then the remaining drives are in order, sda, sdb, sdc. I boot sdc which then is hd0 and sda then is hd1, & sdb is hd2.

title        Microsoft Windows 
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

---

### Post by NCLI on 2010-08-19
> **Lazy-buntu said:**
> Okay, so I finished installing Windows 7.

Now my issue is this: if I put the SSD as a higher boot priority Windows 7 boots.

If I put the HDD as a higher boot priority I can boot Ubuntu.

What I want to do is leave the HDD as the highest boot priority and have it point to the Windows boot loader on the SSD, so I can boot either Ubuntu or Windows from Grub.

I guess if I really have to I can flip flop that BIOS settings every time I want to boot Ubuntu, but it would become a pain fast. Any ideas of avoiding that? It seems like that would be he same idea as that link I posted earlier, but maybe I'm getting my labels mixed up. 

I've tried hd1, hd2, and sd2 in the Grub menu.lst lines to no avail.

Sounds like GRUB is installed on the Master Boot Record(MBR) of the HDD, while Windows' bootloader is installed on the MBR of the SSD.

Set the HDD as highest-priority, start Ubuntu, open a termainal, run "sudo grub-update", then restart your computer. Windows should now show up in GRUB.

---

### Post by Lazy-buntu on 2010-08-19
I reverted to GRUB legacy because I had a catastrophic failure with Ubuntu 10.04, so I fell back to 9.04 and GRUB legacy. Also, I'm more comfortable with editing menu.lst and using start-up manager to keep the number of kernels displayed to a minimum.

I've tried sudo update-grub before and no dice.

Also, my current menu.lst is using that hd2 code to no avail.


If all else fails, can I install grub2 in place of grub legacy? I have to be careful though, because part of installing 10.04 and that catastrophic failure was the corruption of my MBR.

---

### Post by Lazy-buntu on 2010-08-19
Ok, I've updated to Grub2 reluctantly. 

Ubuntu still boots fine. Windows won't boot like before. It keeps saying BOOTMGR not found.

If I make the SSD a higher priority than the HDD, it boots fine with Window's bootloader.

---

### Post by jtarin on 2010-08-19
> **Lazy-buntu said:**
> Ok, I've updated to Grub2 reluctantly. 

Ubuntu still boots fine. Windows won't boot like before. It keeps saying BOOTMGR not found.

If I make the SSD a higher priority than the HDD, it boots fine with Window's bootloader.Another solution is to use EasyBCD installed in windows,(point at Grub, Lilo etc; then it uses the win bootloader to boot all OS's. I've dual booted for more years than I can count and this has been the most recoverable method I have come across....for both Windows and Linux.

---

### Post by Lazy-buntu on 2010-08-19
I think I may do that. I used EasyBCD back in my Vista days, but had to drop it when I upgraded to 7. I heard EasyBCD has a 7 version now, so I'll give it a whirl.

Is there a new way to get rid of the multiple kernels on Grub2 these days?

---

### Post by oldfred on 2010-08-19
If you are getting bootmgr not found that means grub has worked and you are in windows. It is a windows issue. You may need to use windows bcdedit or other repairs.
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by Lazy-buntu on 2010-08-19
> **jtarin said:**
> Another solution is to use EasyBCD installed in windows,(point at Grub, Lilo etc; then it uses the win bootloader to boot all OS's. I've dual booted for more years than I can count and this has been the most recoverable method I have come across....for both Windows and Linux.

That did it, thanks! It's not the most elegant solution, but it'll do.

I don't mean to derail the thread now, but is there an easy way to configure Grub2? I want to remove old kernels from the list and if possible give it a boot splash or background image.

---

### Post by Lazy-buntu on 2010-08-19
> How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)


Thanks I'll try this. I'm shying away from bootrec, bootsect, fixboot, and other Windows commands  because back in May I had a pretty rough experience with install Grub2 to the wrong area and it was a nightmare. EasyBCD will work for me; now it's just about fixing up Grub2 to not look so fugly lol.

---

### Post by jtarin on 2010-08-19
> **Lazy-buntu said:**
> Thanks I'll try this. I'm shying away from bootrec, bootsect, fixboot, and other Windows commands  because back in May I had a pretty rough experience with install Grub2 to the wrong area and it was a nightmare. EasyBCD will work for me; now it's just about fixing up Grub2 to not look so fugly lol.

From the Docs:
> Removing Entries from Grub 2
Entries should be removed by editing or removing files in the /etc/grub.d folder. The /boot/grub/grub.cfg file is read-only and should not normally require editing.

    * Automatically.
          o Too Many Kernels? Kernels removed via Synaptic or with "apt-get remove" will automatically update grub.cfg and no user action is required.
                + In Synaptic, type the kernel number in the search window at the upper right (for example - 2.6.28-11).
                + Find the "linux-image" and "linux-headers" files for the applicable kernel (example - linux-image-2.6.26-11 or "linux-image-2.6.26-11-generic).
                + Right click and select "Mark for Complete Removal" and then press the Apply main menu button.
                + The kernels will be removed from your system and from the Grub menu.
                + If you are not sure of the kernel you are currently using, in a terminal type "uname -r".
                + Many users keep one previous kernel on the machine which previously ran without problems.
          o Other Operating Systems which have been removed from the computer will also be removed from the menu once "update-grub" is run as root.
          o To prevent one of the /etc/init.d files from running, remove the "executable" bit.
                + Example: If you don't want to see the "Memtest86+" entries, run this command:
                  Code:

                  sudo chmod -x /etc/grub.d/20_memtest86+

                + Run the update-grub command to allow the changes to be incorporated in grub.cfg

---

