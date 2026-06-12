---
title: "Ubuntu install trashed my Windows XP MRB"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Peadarm on 2010-02-28
I thought I'd give Ubuntu a try, so downloaded the latest cd (ubuntu 9.10 "Karmic Koala" - Release i386) a month ago and installed it (I thought) as dual boot on my windows pc.

Result is that I can't boot into windows any longer - 0x0000007B blue screen in every possible boot mode. Also Linux 2.6.31-14-generic etc won't start from the gnu grub menu (gives a "no such device" error) - or if I choose windows boot from sda1 here, then pick Ubuntu from the dual boot menu instead of windows..I just get a gray screen. It does run straight from the CD, so I can see my data is at least all still there. For now. I haven't done a full chkdsk coz I'm wary of making things worse.

I've followed online instructions to use the liveCD to repair the mbr, but the cd doesn't seem to have lilo on it, and I can't install ms-sys (get doesn't work coz PC isn't connected to the internet, when I copied ms-sys-2.1.3 it didn't recognise *make*. I didn't get far with the MBR tool on the ultimate boot cd I downloaded.

I appreciate this presents as a windows problem - but it was created by installing ubuntu. I thought I followed the instructions, maybe I did something wrong in terms of partitions (?) - but I didn't expect installing ubuntu to trash my computer. Can anybody help me repair the MBR and get my computer booting from its HDD again??

---

### Post by jerrrys on 2010-03-02
hi peadarm

ubuntu usually works out of the box these days, but seems you hit some bad luck.  i haven't run windows for a while, but seems you can restore windows with your restore disk.  may be wrong about that, like i said its been a while.

---

### Post by HereInOz on 2010-03-02
Have a go at:

Insert your Windows XP CD
When prompted, choose the option to repair the system using the Recovery Console.
Log on to the Windows install on drive c: (assuming that is where you put it) - you will need the administrator password for this.
Once you get into the Recovery Console - a DOS prompt kind of affair, type in:
FIXMBR
then press Enter and answer yes to the dire warnings
then type in:
FIXBOOT
then press Enter.

Then exit from the Recovery Console.

If that works, sweet.  If it doesn't, you have lost nothing.

---

### Post by NightwishFan on 2010-03-02
If you do not have a Windows disk, you can repair using Super Grub Disk. Just burn to a CD, reboot to it, and choose the option Fix Boot Of Windows.

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso)

---

### Post by cariboo on 2010-03-02
Microsoft suggests that you run chkdsk on the drive to repair it. Try [UBCD4Win]("http://www.ubcd4win.com/"), You can boot into a Live CD and run chkdsk on the hard drive. You do need a computer running Windows to create the boot disk.

---

### Post by Peadar on 2010-03-07
Thanks for all the helpful replies. One of the many frustrations of running Windows is that OEMs don't generally provide installation or recovery disks. I just don't have one - and the installation files aren't even on disk - one of the super boot cds I tried to download needs them to complete the disk. Would running chkdsk or scandisk (it's FAT-formatted) repair this mbr, as it's definitely a clash specifically caused by ubuntu installation (rather than hdd problems)? Also, I ran the supergrub disk and the fix windows, but it throws up the message "BootSector Write! VIRUS: Continue (Y/N)?". I'm tempted to press Y, as i don't think it's a virus, but if it thinks it's a virus rather than a corrupt mbr then is it going to do any good?

The other thing I did look into was [using the liveCD to fix the MBR]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") - but like I said, I can't access the internet and can't 'make' ms-sys.

---

### Post by lkraemer on 2010-03-07
Well, right now you have everything to lose.....BE VERY CAREFUL
What you do!

Cause of the Error 0x0000007B

These error messages are generated if your PC is facing one of the following problems:

Boot-Sector Viruses

A boot-sector virus may prevent your Windows system from running normally and generate the Stop 0x0000007B error. This is the reason why, when you receive the error, you may use a reliable and efficient antivirus tool, such as Anti-Virus Plus to scan the boot sector of the hard disk and remove any viruses from it, if detected.

If the error message occurs during Windows Setup, you must delete all the existing partitions from the system if possible, and then recreate the partitions to ensure that all unwanted data including viruses are eliminated from the hard disk.

Device Driver Issues

A miniport driver is required by your Windows XP operating system to communicate with the hard disk controller that is needed to boot your system. The following problems may occur with this device driver and may generate the Stop 0x0000007B error on the system:

    * A device driver required by the boot controller of your PC is not setup to load during the startup.
    * A device driver required by the boot controller of your PC is corrupt.
    * In the Windows registry the information on how to load drivers during system startup is corrupt.

To repair this problem, you may have to replace the faulty driver with a valid and compatible driver. You may also use a reliable registry cleaner tool, such as RegGenie to fix any problems within the registry.

Hardware Issues

Conflicts, such as conflicts between boot controllers and other system controllers or conflicts between different SCSI devices, may also generate the Stop 0x0000007B error on the system. Additionally, the error message may be displayed due to problems with driver translation processes.

Some of the tasks that you can perform to troubleshoot this issue are:

    * Remove any hardware that you would have recently added to the system to see if it is causing resource conflicts on the system.
    * If you have SCSI devices on the system, ensure that the SCSI chain is correctly terminated. Also, remove any non-essential SCSI devices from the computer.
    * Ensure that device translation on your system is turned on.

Miscellaneous Issues

Some of the other causes of the Stop 0x0000007B error are:

    * The boot volume on the hard disk is damaged or Windows XP is unable to initiate it. To resolve this issue connect your hard disk to another computer that is running the Windows XP operating system and then run the chkdsk command on this disk to repair any errors on it. You may also try to install Windows XP in a different folder.
    * You are attempting to install Windows XP on a mirror partition that was initially created using Windows NT. Because Windows XP does not support the Ftdisk volume sets that are created using Windows NT, the stop error is generated. To resolve this issue, you need to change the volumes to a configuration that is supported by Windows XP. For instance, if you are using Windows 2000, change the Ftdisk volumes to dynamic volumes, and if you are using Windows NT, back up your data, break the mirror, and then upgrade to Windows XP.

If I were in your shoes, I'd be going to a friends house and burn the following LiveCD's:
Supergrub Ver .9799, Gparted, Clonezilla, UBCD, and Ubuntu
Boot from the Supergrub LiveCD, Use the HELP selection and fix
the Windows XP Boot sector.  That should get you to where you can at
least boot into XP.  If so, then RUN your Anti-virus program to
VERIFY the Drive is CLEAN.  If not CLEAN, I'd then continue by reading
up on how to repair from this site:
[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)
while using Clonezilla to copy the existing drive to another new Drive.
That way you can be sure you won't lose any of your Data/Files/Software.

Since your system was preloaded, readup on this information:
[http://www.howtohaven.com/system/createwindowssetupdisk.shtml](http://www.howtohaven.com/system/createwindowssetupdisk.shtml)

Or, maybe something here might apply:
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

If you had a M$ Windows CDR you could always try this:
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)

Last but not least, you could purchase a New Drive, Install Ubuntu on
it, and then connect your Windows XP Drive, and copy the Data Files to
Ubuntu at your leisure.

lk

---

