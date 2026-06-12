---
title: "Making a partition for windows in Ubuntu 9.04"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by wiquiwaqui on 2009-08-12
How do I set up a partition for windows XP with ubuntu 9.04 installed already? Will all my files get deleted? Do I use Gparted? Sorry im a noob.

---

### Post by jmac0101 on 2009-08-12
I am also kind of a noob, but I would use Gparted to resize the current partition and place the windows OS on the space you carved out. One thing that might become a problem is that windows might want to start automatically without giving Ubuntu a chance. I ran into this problem before and have always found it easier to install windows first and then Ubuntu (this way the grub bootloader will give you the option of which OS to start in). 

I use Ubuntu for all my computing needs, but often for work and school I am forced to use windows (or at least windows products). I chose not to dual boot, instead I use virtual box and install and run windows while still using my Ubuntu.

Check it out.
[http://www.youtube.com/watch?v=xGI5lOOqMEA&feature=player_embedded]("http://www.youtube.com/watch?v=xGI5lOOqMEA&feature=player_embedded")

---

### Post by pizza-is-good on 2009-08-12
> **wiquiwaqui said:**
> How do I set up a partition for windows XP with ubuntu 9.04 installed already? Will all my files get deleted? Do I use Gparted? Sorry im a noob.
 
It's no problem that you are new.
 
Please give more info on your system. Dual boot? Partitions? Partitions' sizes? All that you can provide. Then it will be easier to help.

---

### Post by Bachstelze on 2009-08-12
It's true that the Windows installer will overwrite GRUB without asking you anything. However, it is possible to reinstall GRUB without reinstalling Ubuntu altogether:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jmac0101 on 2009-08-12
> **HymnToLife said:**
> It's true that the Windows installer will overwrite GRUB without asking you anything. However, it is possible to reinstall GRUB without reinstalling Ubuntu altogether:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Cool! thanks for the info.

---

### Post by wiquiwaqui on 2009-08-12
My system is an HP dv1000 and when I run GParted it seems that the only thing I can do is make a partition table which would erase everything. 

On GParted i think it says that I have 3 partitions???
Partition            File System      Size        Used          Unused          Flags
/dev/sda1            ext3             91.76gb     16.76gb       75.99gb        boot
/dev/sda2             extended      1.39             ----              -----
/dev/sda5            linux-swap     1.39

---

### Post by pizza-is-good on 2009-08-12
Gparted can only work on unmounted partitions, so whatever you do you need to do it through a liveCD.
Then shrink your current partiton, and format the rest as NTFS. Then you should be able to install Windows.

---

### Post by Arand on 2009-08-12
I seem to recall something about XP stubbornly having to be installed on the first partition, so you might want to take that into consideration when repartitioning.

- Arand

---

### Post by raymondh on 2009-08-12
> **Arand said:**
> I seem to recall something about XP stubbornly having to be installed on the first partition, so you might want to take that into consideration when repartitioning.

- Arand

You can always trick windows into thinking it is "first" by editing in the menu.lst.

[Herman's site]("http://members.iinet.net.au/~herman546/p15.html") on GRUB has a lot of tips, mapping, included.

Happy Ubuntu-ing.

---

### Post by Bartender on 2009-08-12
How tough would it be to just reinstall Ubuntu?  Copy your personal data off to some external storage, make a few notes about what you've installed, and wipe it?  You may find that much easier than trying to swim upstream by installing Windows after Ubuntu.

If you take the well-trodden path...

1) Download and burn to .iso the latest stable version of GPartedLiveCD (GPLCD).
2) Set the PC to boot from optical and see if the GPLCD disc boots up and shows you your partitions.
3) Using GPLCD, wipe all partitions.  Each time you give GPLCD a task, apply that task.
4) Create a primary NTFS partition for Windows. Apply.
5) Create an extended partition from the rest of the space.  At this point you could set up your Linux partitions if you wanted, but you don't have to.  You can just leave the space inside the extended partition unformatted. 

Install Windows.  The Windows disc will only see the NTFS partition, leaving the rest of the HDD alone.

Pop in your Ubuntu CD.  The simplest method would be to let it detect and install to the "largest free space", although you could also go manual and set up /, /home, and swap partitions if you felt like it.

---

### Post by Arand on 2009-08-13
I would say that doing a wipe-reinstall is an unnecessary hassle in this case. It might be slightly simpler, but will most likely take much longer, whilst in the end achieving the same result.
- Arand

---

### Post by Mark Phelps on 2009-08-13
+1 on the GParted LiveCD.

You can always get the latest version at distrowatch.com.

You can also download and burn Parted Magic. Has much the same utilities but there have been cases where parted magic worked when GParted did not.

---

### Post by vegesm on 2009-08-13
Before installing XP set the linux partition hidden in GParted. Then XP name his partition as C:. It's good because some programs automatically install themselves at C: (and in XP you can't change the name of the drives). After installation delete the hidden flag from the linux partition.

---

### Post by charles.e.murray on 2009-08-13
> **wiquiwaqui said:**
> How do I set up a partition for windows XP with ubuntu 9.04 installed already? Will all my files get deleted? Do I use Gparted? Sorry im a noob.
It might be wothwhile looking at this website if you want a dual boot with windows and ubuntu [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by wiquiwaqui on 2009-08-13
I keep trying to install XP but it keeps saying set up did not find any hard disk drives installed in your computer. What should I do now?

---

### Post by Arand on 2009-08-14
Just a hunch: It may be that the drive is using AHCI (see [http://www.mydigitallife.info/2007/10/23/windows-xp-setup-could-not-detect-and-find-any-sata-hard-disk-drive-on-ahci-mode/](http://www.mydigitallife.info/2007/10/23/windows-xp-setup-could-not-detect-and-find-any-sata-hard-disk-drive-on-ahci-mode/) )

In that case, you might be able to just disable it through the BIOS, although I don't know if that will mess with ubuntu. Or you could look about for guides on how to get the proper drivers for the XP installer to handle AHCI.

- Arand

---

