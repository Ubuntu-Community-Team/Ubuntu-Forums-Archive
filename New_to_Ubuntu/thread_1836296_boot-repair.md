---
title: "boot-repair"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by hazmat74 on 2011-08-30
Hello, I just installed Ubuntu (11.04) from cd onto a brand-new 2 TB hard drive. It is the only drive on the system. The installation of bootloader failed and I chose to continue installation of Ubuntu and manually repair the bootloader.

I followed the instructions mentioned here: [http://ubuntuforums.org/showthread.php?t=1598478](http://ubuntuforums.org/showthread.php?t=1598478)

and these did not work. I was able to install grub, but I could not run update-grub:

sudo mount /dev/sda2 /mnt
sudo bash
cd /mnt/
chroot .
update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

Also on reboot it just goes straight into grub prompt. 

I stumbled upon Boot-Repair in this forum and it looked promising, but the most current version of the tool is somewhat different looking from what is described here:

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

needless to say I installed it off the live-CD and ran the standard repair. In subsequent tries I looked at the advanced options and they appeared to be set up correctly. The 'Grub Location' and 'Grub Options' were greyed out so there's nothing to do there. It appears that Boot-Repair recognizes the root partition (sda2) correctly and the location of the MBR, sda. In any case, I can't get it to work. Here's the output from Boot-Repair:

[http://paste.ubuntu.com/678429/](http://paste.ubuntu.com/678429/)

If there's a solution to this problem, with or without Boot-Repair, I would appreciate your help.

---

### Post by dolphin194 on 2011-08-30
I've had this problem before, and in my opinion the most simple way that would be effective is to reinstall ubuntu since you just installed it.

---

### Post by jtarin on 2011-08-30
The most straightforward way is to use the CHROOT method as outlined [here]("https://help.ubuntu.com/community/Grub2#ChRoot").
My question would be what did you do initially to prepare this disk for Ubuntu installation and what tools did you use?

---

### Post by oldfred on 2011-08-30
Are you just using gpt partitioning with BIOS or are you using UEFI to boot?

I have BIOS and gpt. With the bios_grub partition I have no issue & grub just installs.

But those trying UEFI seem to have some issues. I also think with UEFI the efi partition has to be the first partition where the bios_grub can be any partition. And with UEFI you do not need the bios_grub partition.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Updates - Avidanborisov created compile script
[http://ubuntuforums.org/showthread.php?t=1772310](http://ubuntuforums.org/showthread.php?t=1772310)

---

### Post by hazmat74 on 2011-08-31
I haven't solved the problem yet. These suggestions were helpful in diagnosing the problem though.

I have an old computer. It has 64b AMD Athlon. I did nothing to prepare the HD, just plugged the live-CD in and let'er rip, as I have always done in the past with Debian installs. It seems that Ubuntu by default wants to create a bios-grub partition of type EFI, which unfortunately is not recognized by my MB.

I am currently attempting to re-install Ubuntu, but this time I have manually partitioned the disks. I have one giant partition mounted on / as ext4 and the remaining space is designated as swap. So far, the installation of the bootloader failed, so I am going to attempt to install it manually again (as per jtarin's link), this time with the new partition table. I'll let you know if that works.

---

### Post by jtarin on 2011-08-31
If your still having problems with EFI there is a solution.....grub2-efi. You can find it in the repositories.

---

### Post by oldfred on 2011-08-31
Do not mix efi partition with bios_grub partition in gpt type of partitions. With larger drives and no Windows gpt is prefered over MBR(msdos) type partitions, but you have to have a small bios_grub partition. 

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.


Also grub does not seem to work with one very large root partition. I suggest a smaller (25GB) / (root) partition and then create a larger /home. Not sure if you will want other partitions. 

If you think you will ever install Windows on this drive do not use gpt as Windows 7 will only use gpt with UEFI boot on new systems.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

If you want to convert back to MBR you have to houseclean bits of gpt that may remain first.
Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

---

### Post by hazmat74 on 2011-08-31
I can try an installation with separate /root and /home partitions, but isn't EFI compatibility (which I lack) still a problem? Is there a way to install the bootloader without defining any EFI-type partitions, as these will be ignored by my Motherboard/OS?

no Windows7 :-)

---

### Post by oldfred on 2011-08-31
UEFI and BIOS are two totally different ways to boot. The very new systems have UEFI but seem to always have a BIOS boot capability and call everything BIOS.

Older system still use BIOS which has been the standard since the IBM PC started in the early 1980's.

Partitioning is separate from BIOS & UEFI. Somewhat. Windows 7 will boot from UEFI but has to have gpt.

I have BIOS and use gpt on my Ubuntu boot drive, MBR on my XP drive and am planning on converting in place my larger MBR drive to gpt.

---

### Post by srs5694 on 2011-08-31
> **hazmat74 said:**
> I can try an installation with separate /root and /home partitions,

I want to be absolutely crystal clear about one point: Every Linux installation requires a "root partition", which is often written as "/". This partition contains, among other things, a directory called /root, which is the superuser's home directory. (It'll normally be nearly empty on an Ubuntu system.) Most directories in Linux can be split off into their own partitions, and technically, /root can be so split off, but generally shouldn't be. Thus, you almost certainly do *not* want a separate /root partition, but for various reasons, you probably *do* want to separate root (/) from /home. This terminology can be confusing, and chances are you were thinking the right thing, but communicating it unambiguously can be another matter.

> but isn't EFI compatibility (which I lack) still a problem? Is there a way to install the bootloader without defining any EFI-type partitions, as these will be ignored by my Motherboard/OS?

no Windows7 :-)

There are two issues, which Windows ties together, but that Linux does not:


[list]
[*]**Firmware type** -- Older x86 and x86-64 computers and some new computers use BIOS as the firmware, whereas many new computers use EFI or its updated cousin, UEFI. (Today, EFI is mostly on Macs, whereas many new PCs use UEFI.)
[*]**Partition table type** -- The MBR partitioning system is roughly as old as the PC (30 years), and is nearing limits beyond which it can't be pushed. The replacement system is GPT, which is a practical necessity on most disks over 2 TiB in size.
[/list]


Under Windows, if your computer is BIOS-based, you *must* use MBR partitions, and if your computer boots in UEFI mode, you *must* use GPT partitions. Most, and perhaps all, modern UEFI implementations support a BIOS compatibility mode, so you can boot such UEFI-based computers using either BIOS mode and MBR partitions or UEFI mode and GPT partitions. Switching Windows between those modes is tricky, though. Linux is not so limited; you can boot either a BIOS-based or a UEFI-based computer using either MBR or GPT partitions. On a UEFI-based computer with BIOS compatibility support, you can (relatively) easily switch the boot mode by installing an appropriate boot loader and switching the boot mode in the firmware setup utility. FWIW, I'm typing this on a system that uses BIOS with GPT.

Within the GPT system, there are two special partition types that are associated with system boot operations:


[list]
[*]**[BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition)** -- This is a partition that's used by GRUB 2 on BIOS-based computers. It's typically small -- as small as about 30 KiB, although 1 MiB is a more common size because of the common 1 MiB partition alignment policy today. This partition is unnecessary on UEFI-based computers and on computers that don't use GRUB 2. (Some other boot loaders have their own special partition types, though.)
[*]**[EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition)** -- This is a FAT partition that holds files that the EFI (or UEFI) can read, including boot loader files. The ESP is typically 100-200 MiB in size, although I favor sizes at the high end of that range or even a bit higher (200-300 MiB) because the [ELILO](http://elilo.sourceforge.net) boot loader works best with the Linux kernel on the ESP, and a small number of kernels can completely fill a small ESP pretty quickly. The ESP is not required on BIOS-based computers.
[/list]


Having the "wrong" type of partition (an ESP on a BIOS-based computer or a BIOS Boot Partition on a UEFI-based computer) does no harm, aside from chewing up a bit of disk space -- and these partitions are small enough that I wouldn't worry about that. If you lack the required type, though, the computer might not boot or booting might be unreliable. Thus, if you're using GPT and are in doubt about how your computer is booting, I recommend creating both a BIOS Boot Partition and an ESP. I'd make the ESP partition #1 and the BIOS Boot Partition #2, if that's convenient, although this ordering isn't really critical. None of this applies if you use MBR and BIOS booting, although if you use MBR and UEFI booting, you do need an ESP.

You mentioned "motherboard compatibility," but traditionally, the BIOS has been simple enough that it doesn't even read the partition table; that's been the job of the boot loader and OS. Some modern BIOSes, however, do make the attempt, and some of these [have bugs](http://www.rodsbooks.com/gdisk/bios.html) that can complicate booting from GPT disks. To the best of my knowledge, these bugs all have workarounds. The most common (on some Intel-branded boards) can be worked around by setting the "active/boot flag" on the MBR's protective partition (part of a standard GPT setup) using Linux's fdisk utility. (Do *not* use parted, GParted, Palimpsest Disk Utility, or any other GPT-aware utility to do this, though; they'll modify GPT data structures rather than the protective MBR that you need to modify to work around this bug.) At least some of the Intel boards that are affected by this bug are UEFI-capable, so you can boot them in UEFI mode, too.

I hope this helps to clarify some of what's going on with BIOS vs. UEFI and MBR vs. GPT issues.

---

### Post by hazmat74 on 2011-09-01
Well folks, I'm at my wits' end. I've attempted to install Ubuntu twice since yesterday following the suggestions above, but didn't get anywhere because the installer crashes. I've never had so much difficulty installing Linux before on a blank hard drive. It seems like this is a major bug, and a pain in the you-know-what. I'm sure I'm not the only one out there trying to put linux on a BIOS-only computer.

---

### Post by jtarin on 2011-09-01
[You might try the alternate installer CD.]("http://www.ubuntu.com/download/ubuntu/alternative-download")

[Here are some musings on the GRUB2EFI, which might be informative.]("http://blog.fpmurphy.com/2010/03/grub2-efi-support.html")

[Additional hints.]("https://wiki.archlinux.org/index.php/GRUB2")

---

### Post by oldfred on 2011-09-01
Are you installing to gpt partitions and have the grub_bios. Or MBR partitions. But if you ever had gpt you have to houseclean out all the old gpt data. Same with RAID, if drive was ever set to RAID then it saves internal data that you have to houseclean out.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo sfdisk -d /dev/sdc > parts.txt

Missing Partitions in GParted - repairs info:
Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda

---

### Post by hazmat74 on 2011-09-02
okay here's what worked (its a combination of some of your guys' suggestions):

**step 1**: wipe the hard drive, partition table, completely blank and unformatted.
**step 2**: boot into Ubuntu off the live-CD, going directly into the installation, NOT the "try Ubuntu" option. Something weird happens if you try this after prior attempts. Also, THIS IS IMPORTANT, do NOT check the "install updates" option at the beginning of installation help wizard. Take care of that later.
**step 3**: create the following partition table:
/dev/sda:
/dev/sda1 - 10mb unformatted (you can't set flags from the installer, unfortunately)
/dev/sda2 - 30 GiB ext4, mounted at /
/dev/sda3 - 2 GiB swap
/dev/sda4 - the rest (1.97 TiB), ext4, mounted at /home
**step 4**: finish installation, then reboot live-CD after (expected) failed bootloader installation
**step 5**: open Gparted, edit the 10mb boot partition so it has the "bios_grub" flag. update and re-install GRUB, reboot.
**step 6**: air guitar

:guitar:

---

### Post by tsucol11 on 2011-09-02
This was an interesting read.

Thanks

Brian

---

### Post by oldfred on 2011-09-02
Glad you figured it out.

I installed to gpt and had no issues, but I always create partitions in advance & had set the bios_grub flag before the install. Then it worked just like any manual install and grub was correctly installed.

---

### Post by YannBuntu on 2012-01-13
Hello
someone needs help for a similar case (EFI session, but no GPT): [http://ubuntuforums.org/showthread.php?t=1908511](http://ubuntuforums.org/showthread.php?t=1908511)

and, in a general way, i need help to improve Boot-Repair's EFI support: [https://blueprints.launchpad.net/boot-repair/+spec/improve-efi-support](https://blueprints.launchpad.net/boot-repair/+spec/improve-efi-support)

thanks

---

