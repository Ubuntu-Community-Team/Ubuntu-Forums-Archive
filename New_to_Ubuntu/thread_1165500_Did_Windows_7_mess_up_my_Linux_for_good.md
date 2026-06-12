---
title: "Did Windows 7 mess up my Linux for good?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by steve04 on 2009-05-20
Ok here is my situation.  I originally was triple booting Windows XP, Windows Vista, and Linux Mint KDE.  (that is the order I installed them).  Later on I decided to try Windows 7.  I deleted the XP partition and installed Windows 7 in it.  This deleted GRUB as well as access to Vista.  My computer automatically booted into Windows 7.  I inserted the Vista disk and did a recovery and was then able to choose beween 7 and Vista.  Next I wanted to get back my version of Linux and attempted to boot from a live cd and go to the terminal.  For some strange reason I can no longer boot off of any of my Linux CDs.  I have tried Ubuntu 8.10, Linux Mint, Ubuntu 9.04, and even PC Linux.  I get to the screen where you can choose to boot from cd, install, etc.  When I select boot from CD, it will bring up the loading screen (Ubuntu with the orange bar on the bottom that scrolls for example) but once this is finished the screen goes black and it never comes on.  I even let it sit for 4 hours today and it never came up.  My computer freezes so bad that I have to hold down the power button on the tower to get it to turn off.  I have a LG DVD drive as well as the Xbox 360 HD DVD drive and neither will let me boot into the Linux live cd.  Did Windows 7 somehow make it so I can no longer use Linux?  Before I installed W7 , I could boot from the Linux cds because I had a distro installed.  Sorry if this sounds confusing.. it makes no sense at all to me.  Can anyone help??

---

### Post by khelben1979 on 2009-05-20
I can't give you any other advice on this, other than I believe that it's better if you wait until the first stable release of Windows 7 comes out and then you install Windows first and Linux afterwards. (I've heard that it should do the trick)

I haven't tried Windows 7 myself yet and see no reason to why either.

---

### Post by bennachie on 2009-05-20
That's really odd. I have recently installed the Windows 7 Release Candidate on my Compaq laptop which was running Vista and Ubuntu 9.04. In my case, however, I simply installed Windows 7 in place of Vista, having no need for more than one instance of the dark side).

I then had no difficulty in booting from the Ubuntu LiveCD, opening a terminal, and rebuilding the Grub loader so that normal Ubuntu service could be resumed.

Accordingly, I don't think that this odd effect necessarily has anything to do with the installation of Windows 7 per se. The whole business is very puzzling. Although nothing that a Vista recovery disk did would surprise me - for example, I would expect it to tramp all over an Ubuntu partition in pursuit of the holy grail of the "original factory settings" - that should not prevent you from subsequently booting from a LiveCD. Of course, you might not be able immediately to install Ubuntu from the LiveCD if the Vista disk had messed up the partition settings, but that would be a completely different issue.

I'll look forward to the comments from other more knowledgeable contributors.

Incidentally, Windows 7RC appears to be perfectly stable, and is definitely quicker and tidier than the original version of Vista, but the whole setup remains pretty clunky and uninspiring by comparison with Ubuntu or Linux Mint.

---

### Post by whitethorn on 2009-05-20
Hi, I have also installed Windows 7 RC. I had some problems getting grub back, but that's only because I have my Ubuntu installed on a Raid 0.  As far as I know it should not have changed anything to cause boot problems.  I used a usb stick with ubuntu live cd on it.  I used unetbootin to get my usb stick bootable.  You could also give that a try if your motherboard supports booting from an USB.

---

### Post by steve04 on 2009-05-20
Yeah I can't figure it out.  I really don't want to re-install Linux because I have a ton of headers for Giganews downloaded and everything is working good.  I have also tried a Windows program called Easy BCD.

I add the Linux option and it displays my drives as the following..

Drive 0 (this is my primary drive where all OS's are)
Partition 0 (NTFS) 146 GB - - This is Windows 7
Partition 1 (NTFS) 195 GB - - This is Windows Vista
Partition 2 (Linux Native) 121 GB - - This should be Linux Mint
Partition 3 (Linux Swap) 3 GB

Drive 1 (storage drive)
Partition 0 (NTFS) 699 GB

Drive 2 (storage drive)
Partition 0 (NTFS) 466 GB

Drive 3 (no clue what this is)
Partition 0 (BIG DOS - Fat 16) 0 GB



When selecting to add Linux to BCD I can select a box that says GRUB IS NOT INSTALLED TO THE BOOTSECTOR.  If I don't pick this when I select Linux from the Windows boot loader, it says Grub4Dos and takes me to a command prompt that says Grub>. If I do check that box it says "Cannot load from hard drisk.  Insert systemdisk and press a key."


Name:  NeoSmart Linux
BCD ID:  {b2577cb6-3d37-11de-81b4-efa89e0d4c21}
Drive:  D:\
Bootloader Path:  \NST\nst_grub.mbr


That is what the options look like for the Linux entry.  I'd imagine the problem is that it's pointing to D:\ but even changing this doesn't work!  Any help would be greatly appreciated because I really don't want to lose my Linux...

---

### Post by Axis on 2009-05-20
It only makes sense that this would be a hardware problem?

In boot order try and remove the hdd altogether and then just allow for the booting of your disc drive. See how that works for ya?

Best of luck,
Axis

---

### Post by nhasian on 2009-05-20
just for troubleshooting purposes, can you either disable your hard disks from the bios or unplug the sata/IDE cable from the drives and try to boot from the ubuntu CD again?  this is a quick way to find out if one of the hard disks or partitions is preventing ubuntu from loading.

---

### Post by steve04 on 2009-05-23
I think this is hopeless.  I disabled every one of my hard drives and am still having the same problem.  I have tried booting from 2 different CD drives so I don't think thats the issue either.


Note:  Also when I put the boot cds in the drive from Windows they show up as the Ubuntu CD.. so I know they can be read.

---

### Post by ronparent on 2009-05-24
I've created several ubuntu labled coasters. Your best bet seems to be to try burning a new cd (or perhaps a dvd). Being able to read the directory doesn't mean that you can read all the data necessary to boot.

---

### Post by Mark Phelps on 2009-05-24
When you installed Vista after XP, it wrote its boot files to the XP partition -- that's how it works on multiboot machines.  When you erased the XP partition to install Seven, you erased the Vista boot files.  Which is why Vista would then not boot anymore.

As to Seven destroying your ability to install Linux or boot from CDs DVDs, I have a multiboot machine with Seven, Vista, and several versions of Linux -- and all of them boot just fine and read any CD or DVD I insert in the drives.  So, there is not a generic problem with Seven (or any other MS OS) either (1) making your CD/DVD drive not bootable anymore, or (2) preventing the install of a Linux OS.

---

### Post by steve04 on 2009-05-25
Well I got things figured out.  I have dual monitors so that was causing the issue with the live CD.  Unfortunately I still was unable to bring grub back.  I deleted the Windows 7 partition and was unable to recover Vista (using the boot cd) or recover grub (using a live ubuntu cd).  Fortunately I was able to use the now working live Ubuntu cd (since I unplugged 1 of my monitors) to copy my .pan2 directory (newsgroups headers) to another drive.  I reinstalled XP, Vista, and Ubuntu 9.04 and am now back in business.  So for future reference, if you have dual monitors make sure to unplug one before running Linux from a live cd.  I'm just going to stay away from Windows 7.  I'm just going to stick with XP and Linux (only going to use Vista for games that require it, if there are any).  Thanks for the help all.

---

