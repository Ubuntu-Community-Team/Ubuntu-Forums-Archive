---
title: "Cannot install as per the docs: Please help!"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Dog walker on 2009-06-25
Could someone please help with some basic installation questions, as you can see from below, I have read the docs (to the best of my ability), tried for myself, but I'm stuck for a solution. Any help greatly appreciated.

I'm trying to setup a dual boot system (Jaunty 9.04 & WinXP HE). I have backed up all my data, so I can do repartitioning and load the OS's fresh, but this in itself is giving me problems.

The Ubuntu docs say... "*In order for OpenFirmware to automatically boot Ubuntu the Linux partitions should appear before all other partitions on the disk*." The docs also say..."*you should install all other system(s) before proceeding with Linux installation*." I have no problem understanding the logic here and I admit that I am somewhat anal about getting it right and having a sound base for the OS's individually and as a dual boot system.

Here is the problem as I am finding it: The only way I can install WinXP and at the same time leave partitions for Linux is to create partitions with my Windows installation CD which I am doing as follows:-

C: - 300Mb (reserved for 'root')
D: - 6Gb (reserved for '/usr')
E: - 4Gb (reserved for '/var')
F: - 500Mb (reserved for '/tmp')
G: - 50Gb (reserved for '/home')
H: - 2Gb (reserved for 'swap')
I:  - 50Gb ('Windows')

Partitions C: to H: I leave as RAW so that  Ubuntu can format these during it's only installation, but here comes the problem... as WinXP is being installed into partition I: it also automatically formats partition C: (ntfs) presumably for an MBR, so there goes all my planning and ability to comply with the Ubuntu docs and install Linux into the first partitions. I can't reformat C: after WinXP is installed because it then fails to boot.

Can someone please tell me where I'm going wrong or what I'm not understanding. I realise that I could create an extra partition to allow for the Windows MBR (if I've assumed correctly that this is whats happening), or I could even allow the Ubuntu installer to do an automatic installation on top of Windows, but I trying to follow the preferred configuration as per the Ubuntu docs.

Sorry for the long explaination, but I would really appreciate some help.

Thanks

---

### Post by mcduck on 2009-06-25
Actually you should put Windows in the first partition, as Windows sometimes has problems running if it's not located on first partition of first disk.

For Ubuntu partitions, you don't need to create any at the point when you install Windows. Just make the Windows partition the size you want, and leave the rest of the disk as unpartitioned space.

..and unless you have some specific reason, you are not going to need separate partitions for /usr, /var, /tmp and others like that. Simple root and swap partitions will work fine, add a separate /home partition if you like.

edit: The Open Firmware part in the guide only applies to systems that actually use Open Firmware, meaning Macs, SUN workstations and such. It's not used on normal x86-compatible PCs.

---

### Post by Dog walker on 2009-06-25
> **mcduck said:**
> Actually you should put Windows in the first partition, as Windows sometimes has problems running if it's not located on first partition of first disk.

For Ubuntu partitions, you don't need to create any at the point when you install Windows. Just make the Windows partition the size you want, and leave the rest of the disk as unpartitioned space.

..and unless you have some specific reason, you are not going to need separate partitions for /usr, /var, /tmp and others like that. Simple root and swap partitions will work fine, add a separate /home partition if you like.

Thanks for the reply mcduck.

I'm not disagreeing at all, but the way I am trying to do it with Ubuntu in the first partitions and the extra partitioning is exactly what the Ubuntu docs recommend or am I reading/understanding them wrong!

---

### Post by arochester on 2009-06-25
Have a look at "The definitive dual-booting guide: Windows 7, Linux, Vista and XP step-by-step" on [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by mcduck on 2009-06-25
> **Dog walker said:**
> Thanks for the reply mcduck.

I'm not disagreeing at all, but the way I am trying to do it with Ubuntu in the first partitions and the extra partitioning is exactly what the Ubuntu docs recommend or am I reading/understanding them wrong!

I have no idea what document you are talking about, but you must indeed be misinterpreting the guide or something.

Really, Windows has problems running on any other partition than the first partition of first drive. And the OpenFirmware-part of installing Ubuntu to the first partition only applies to systems using OpenFirmware. Based on the fact that you are trying to dualboot Ubuntu & Windows XP I really doubt you'd be running such a machine.

Having separate parts of the directory hierarchy on separate partitons an be useful n some situation, but separate partitions for directories such as /etc or /user are hardly ever useful on any normal desktop system, and will only your system more complex and hard to administrate, not to mention the problems of deciding exactly the correct sizes for each of these directories to avoid one of them running out of space while some other has plenty f extra free space available.

Assuming you are trying to do a normal desktop install, this guide should have pretty much everything you need to know: [https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by wizard10000 on 2009-06-25
What you've got is a little overkill  :)

I know what the docs say but I'd run Ubuntu with three partitions - root, /home and swap.

Having /var on a separate partition is useful if you're running a server so a runaway process doesn't fill up your boot partition with logfiles and bring the system down but that really doesn't apply on a home PC.  I can't think of any reason to have /usr or /tmp on their own partition on a home PC.

Couple other things to think about, though -

A windows installer will always put its boot files on the partition marked active (the one with the boot flag set) and since that partition must be readable by Windows it'll format it as NTFS if it's too big for FAT32.

I prefer to use a Windows bootloader to start Linux rather than the other way around because that way you can reinstall either OS without trashing your boot sector but that's just my preference and is a little too in-depth for an absolute beginner forum  ;-)

Here's what you do.

1.  Create a 50gb partition for Windows then install Windows.

2.  Run the Ubuntu installer from the live CD - you can select manual partitioning from within the installer - I use a 30gb root partition, a 2gb swap partition and the remainder of the disk for /home.

But - since a hard drive can only have four primary partitions you might want to consider doing it this way instead -

1.  50GB - Windows

2.  30gb - Linux root

3.  2gb - swap

4.  Use this to hold extended partitions

   4a.  Put /home here

Actually you can do it either way.

Good luck -

---

### Post by Dog walker on 2009-06-25
mcduck & arochester,

Thanks very much for the help and the links.

Reading your messages has shown me where I've gone wrong... I had done a search and without looking properly I've been reading the 'PowerPC' docs. Yes I'm an idiot and for my stupidness I've spent a solid 17hrs trying to figure it out. My apologies for wasting time.

I'm off to read the links and the correct docs... thanks very much for putting me on the right track.

Sorry :oops:

Thanks too Wizard10000, just caught your message after I'd replied... thanks.

---

### Post by Dog walker on 2009-06-25
PS: one last question. I am going to read the docs, but if I want to share data files between Win and Linux will the /home partition be suitable or do I need an extra ntfs partition?

---

### Post by Bradtek on 2009-06-25
It will be simpler if you create an NTFS partition to share files with Windows.

Ubuntu can read/write to NTFS by default, but Windows can not read EXT2/3/4 without installing a 3rd party driver.

---

### Post by Dog walker on 2009-06-25
> **Bradtek said:**
> It will be simpler if you create an NTFS partition to share files with Windows.

Ubuntu can read/write to NTFS by default, but Windows can not read EXT2/3/4 without installing a 3rd party driver.

Thank you Bradtek... understood and will do.

---

### Post by mcduck on 2009-06-25
> **Dog walker said:**
> mcduck & arochester,

Thanks very much for the help and the links.

Reading your messages has shown me where I've gone wrong... I had done a search and without looking properly I've been reading the 'PowerPC' docs. Yes I'm an idiot and for my stupidness I've spent a solid 17hrs trying to figure it out. My apologies for wasting time.

I'm off to read the links and the correct docs... thanks very much for putting me on the right track.

Sorry :oops:

Thanks too Wizard10000, just caught your message after I'd replied... thanks.

No problem, we all make mistakes (and most of the times rather stupid little mistakes which is even more annoying.. :D) Hope you get the system running now without any bigger problems.

And, in the end, normal Ubuntu install is actually rather simple process. It's just that the more complete guides tend to have lots of options and configurations that might be needed in some special setup while normal user's don't really need to know about them at all. That makes the process seem a lot more complex than it is (unless you happen to be administrator of some strange server system that needs those special configurations)

---

