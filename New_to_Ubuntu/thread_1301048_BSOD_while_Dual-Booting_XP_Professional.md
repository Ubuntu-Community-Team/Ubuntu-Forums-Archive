---
title: "BSOD while Dual-Booting XP Professional"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Omegaham on 2009-10-25
After using Linux for a while, and getting frustrated over my inability to find a way to play Windows games on it, I finally decided to bite the bullet and install the two operating systems side-by-side. Following the instructions [here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm"), I managed to shrink the Linux partition, and gave around 300 GB of unallocated space for Windows to take up.

I then took my brother's XP CD and tried to install. It goes through setup, and then as it starts Windows, I get a Stop error. Aside from the standard BSOD stuff, (Windows has encountered a fatal error, etc etc etc), it gave the technical information underneath.

STOP: 0x0000007b (0xF78D6524, 0xC0000034, 0x00000000, 0x00000000)

I searched the Internet, and found [this]("http://support.microsoft.com/kb/314082") entry on Microsoft Support, and it seems to be saying that because I don't have the same hardware as my brother's computer, it's getting annoyed with the hardware and crashing. Is there any way to fix this, or do I really need to buy an XP CD?

Thanks in advance.

---

### Post by hansdown on 2009-10-25
Hi Omegaham.

When a copy of windows is installed, one of the things microsoft does, is scan your hardware, so as to enforce their end user license agreement, which does not allow the software to be used on multiple machines at the same time.

[http://proprietary.clendons.co.nz/licenses/eula/windowsxpprofessional-eula.htm](http://proprietary.clendons.co.nz/licenses/eula/windowsxpprofessional-eula.htm)

You need to purchase a new copy.

---

### Post by Omegaham on 2009-10-25
Argh... that's just great. Looks like a trip to Best Buy is in order, then... *sigh*

Thanks anyway.

---

### Post by Omegaham on 2009-10-26
Alright, I looked around town, FINALLY found a basic copy of Windows XP, (they were taking Vista off the shelves to make room for the 200-dollar Windows 7) bought it, and put it in... and it's still giving me this same error.

Would it have anything to do with the way I divided up the partitions? Looking online, the stop error seems to happen also when the hard drive isn't working right. Is there any way to check it to make sure it's working correctly?

---

### Post by isparkes on 2009-10-26
> **hansdown said:**
> Hi Omegaham.

When a copy of windows is installed, one of the things microsoft does, is scan your hardware, so as to enforce their end user license agreement, which does not allow the software to be used on multiple machines at the same time.


I don't think Windows is getting that far - the STOP 7B error is when something is stopping the system from even having a go at a boot.

I think you might need to fix your boot sector. There should be a way of doing this from the recovery disk - try searching for "fix MBR".

---

### Post by Omegaham on 2009-10-26
Alright, using [_this_]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm") tutorial.

Unfortunately, it doesn't even get to the point where I can access the Recovery console. Basically, it starts up, says, "Press any key to boot from CD," (I press the spacebar) installs a bunch of drivers, and then says, "Starting Windows." The screen turns black, then BSODs with the 7b stop error. I don't even get to the screen where it offers to install Windows.
[]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm")

---

### Post by Omegaham on 2009-10-26
Bump with a small update: I found another link online that describes how to create a Windows Recovery disk, but I don't have a floppy drive to use it. Am I up the creek without a paddle if I can't access the Recovery Console?

---

### Post by Omegaham on 2009-10-26
Bump (Sorry if doing that is against the rules)

---

### Post by clive littlewood on 2009-10-26
Hi

I would advise that you format your hardrive and install windows first then let Ubuntu install alongside windows as a dual boot.

If you have data you must recover first see if you can access using the live CD of Ubuntu.

Clive

---

### Post by ctc26 on 2009-10-26
You may find that having Grub installed to your boot sector has confused windows. Perhaps the install cd is crashing because it can't correctly read your HD.

As previously mentioned, try installing windows on a clean partition table (after backing up your data) and then install Ubuntu along side it.

---

### Post by Omegaham on 2009-10-26
Okay, I have nothing on my hard drive that can't be replaced. How would I wipe it and start anew?

---

### Post by H3l0 on 2009-10-26
An easy way of doing it is to download UBCD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/), burn the iso, boot from it, and startup Darwins boot and nuke.  This is done AFTER backing up anything important you might need.  Single wipe with that tool should do the trick.  

After this I would follow the advice of Clive and install XP first, then Ubuntu second.

---

### Post by LewRockwell on 2009-10-26
we just wanted to point out that...unless we've missed it...we don't even know what hardware we're dealing with

and we all know how some hardware/chipsets/firmware is more problematic than others

.

---

### Post by Omegaham on 2009-10-26
Okay, it's downloading now. I'm doing this on a different computer, because I used the Partition Editor to blank my hard drive. GRUB is still there, and seeing as how that's the problem, I'm hoping that UBCD will get rid of it.  Hope this works...

---

### Post by Omegaham on 2009-10-26
Damn, it didn't work. GRUB is still on there; it's almost like it's taunting me...

Any suggestions on getting rid of it?

---

### Post by VampyrByte on 2009-10-26
0x7B is INACCESSIBLE_BOOT_DEVICE
Probably Windows getting confused with the bootloaders. Can also be a problem with automated installations. 

[http://support.microsoft.com/kb/303786](http://support.microsoft.com/kb/303786)

---

### Post by Omegaham on 2009-10-26
> **VampyrByte said:**
> 0x7B is INACCESSIBLE_BOOT_DEVICE
Probably Windows getting confused with the bootloaders. Can also be a problem with automated installations. 

[http://support.microsoft.com/kb/303786](http://support.microsoft.com/kb/303786)

Yes - the problem is that GRUB is sitting in the Master Boot Record and isn't leaving, so Windows can't boot up. I need a way to get rid of it so I can install Windows.

Help would be greatly appreciated.

---

### Post by H3l0 on 2009-10-26
If you can get to the recovery console of XP with the installation disk then try FDISK /MBR.  If you cannot get to the recover console then the UBCD should have some DOS boot disks available to try that piece of code in.

---

### Post by pastalavista on 2009-10-26
If you're starting fresh, boot first with a legal Windows disk and format the drive into two partitions. Install XP on the first partition only and leave the other blank. After it's installed and running right, reboot with the Ubuntu live CD and install it on the blank partition. That's how I would do it.

---

### Post by sandyd on 2009-10-26
> **Omegaham said:**
> Yes - the problem is that GRUB is sitting in the Master Boot Record and isn't leaving, so Windows can't boot up. I need a way to get rid of it so I can install Windows.

Help would be greatly appreciated.
try
```

dd if=/dev/zero of=/dev/sda bs=512 count=1
```
in a ubuntu livecd.

---

### Post by sandyd on 2009-10-26
> **pastalavista said:**
> If you're starting fresh, boot first with a legal Windows disk and format the drive into two partitions. Install XP on the first partition only and leave the other blank. After it's installed and running right, reboot with the Ubuntu live CD and install it on the blank partition. That's how I would do it.
he can't even get to the first page of the winxp OEM disk.

---

### Post by Omegaham on 2009-10-26
I don't seem to be getting anywhere here.

First, I went and completely wiped the hard drive with KillDisk; everything got turned into zeros. I then tried to boot Windows again - no dice, same stop error.

Next, I booted up the UBCD again, booted up a DOS disk, and looked at the contained partition editor - it let me edit the Master Boot Record. It labelled it as "Unknown." I changed that to the first option it gave me. I then saved that, rebooted with the Windows CD in, and tried again. No dice. And now I'm back with the Live CD.

To Carlee: Here's the results of the code you told me to enter:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00866126 s, 59.1 kB/s
ubuntu@ubuntu:~$ 

```Is this a step in the right direction?

Thanks for the help, guys. This is just crazy.

---

### Post by pastalavista on 2009-10-26
> **carlee said:**
> he can't even get to the first page of the winxp OEM disk.
ok then, try booting with the Ubuntu CD and use gparted to delete all partitions and format the entire disk to FAT32... twice. Then try the Windows CD again. This isn't a copy of an XP disk is it?

---

### Post by Omegaham on 2009-10-26
> **pastalavista said:**
> ok then, try booting with the Ubuntu CD and use gparted to delete all partitions and format the entire disk to FAT32... twice. The try the Windows CD again. This isn't a copy of an XP disk is it?

No, I just bought the CD at Wal-Mart.

Gparted doesn't seem to have a FAT32 option, but it does have an MSDOS option. Is that what I'm looking for? I'm clicking Partition > New.

---

### Post by pastalavista on 2009-10-27
> **Omegaham said:**
> No, I just bought the CD at Wal-Mart.

Gparted doesn't seem to have a FAT32 option, but it does have an MSDOS option. Is that what I'm looking for? I'm clicking Partition > New. 

try right-clicking the partition and select 'format to' and FAT32 should be there in the choices, but for a new partition MSDOS should do. NTFS is the 'secure' filesystem used by XP pro. It gets reformatted during install anyway. Any kind of MS or Linux reformat should erase the leftover grub/boot sector, but for installing Windows, it's best to start with a MS format. It can't do anything with a Linux formatted drive.

---

### Post by H3l0 on 2009-10-27
If after these options you still cannot boot into windows startup, try unplugging your hd and starting up Win.   If it still gives you the stop error then we are looking at something BESIDES a hd problem.  IF this is the case lets eliminate some hardware.  unplug all unnecessary hardware,  HD's, all but one stick of ram, etc.  Just the essentials for your computer to boot.  you can also try and swap out your optical drive.  also check the bios to see what your HD option is set to (AHCI, or IDE etc...)  Again, if you unplug the hd, and still get the error then try the above troubleshooting steps.  If you do not get the error, then we KNOW it is the particular HD you are using.

---

### Post by Omegaham on 2009-10-27
> **pastalavista said:**
> try right-clicking the partition and select 'format to' and FAT32 should be there in the choices, but for a new partition MSDOS should do. NTFS is the 'secure' filesystem used by XP pro. It gets reformatted during install anyway. Any kind of MS or Linux reformat should erase the leftover grub/boot sector.

Okay, it's formatting now to Fat32. So after this, I just restart, put in the XP cd, and pray?

Edit: Okay, I might need a little help with disconnecting stuff; I'm nervous about digging around with hardware.

---

### Post by pastalavista on 2009-10-27
yes, prayer can't hurt, haha, but God may have more urgent matters ;)

---

### Post by egalvan on 2009-10-27
If you are still having problems wiping the drive clean, 
I suggest downloading the original  "Darik's Boot And Nuke" ... dban

get the iso from here, it's very small.

[www.dban.org](www.dban.org)


MAKE SURE YOU HAVE NOTHING ON THE HARD DRIVE YOU NEED TO SAVE.
DBAN WILL WIPE THE DRIVE.
THERE IS NO RECOVERY.

burn to a CD, and boot your computer form it.

Accept the defaults, and in a few minutes to a few hours, depending on the size of the drive,
you will have a completely clean drive, 
the same as when it left the factory.

if you still have problems after this step, then you have other problems besides the state of the drive.


I've used dban for over two years, and except for faulty hardware,
it has never failed to sterilize a hard drive.
SCSI, IDE-PATA/SATA, it's all the same to dban.

---

### Post by Omegaham on 2009-10-27
SUCCESS!

I disconnected the hard drive, and it worked. I then reconnected it, and it still worked. I have no idea what happened, but it's doing fine now. Off to dual-boot and end this nightmare...

Thanks again for all your help, guys.

---

### Post by H3l0 on 2009-10-27
AWESOME!  

I don't know what fixed it (prob the FAT32 wipe) but at least it is working!  Good luck on your dual booting adventure!

---

### Post by LunaticHiatus on 2009-10-27
I run windows in virtual machine. its very easy to do, you get near native speed, and doesn't get in the way.

---

### Post by Omegaham on 2009-10-27
> **LunaticHiatus said:**
> I run windows in virtual machine. its very easy to do, you get near native speed, and doesn't get in the way.

I tried that with VirtualBox; unfortunately, I can't get 3D acceleration or my nice video card to work.

I managed to do it; 400 GB for Windows, and 300 for Ubuntu. I love my computer. :)

---

