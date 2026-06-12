---
title: "Can't clear GRUB RESCUE on empty,formatted Volume-FIXMBR etc. not working!"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by emarkay on 2011-08-10
I installed a new hard disk (sda), the other existing (sdb) had Ubnutu.  I needed a clean Win XPSP3 install on the PC, so I used GParted to reformat the Ubuntu volume (empty, even sudoed away the Lost and Found dir) and also reformatted first volume on sda to NTFS, and I also removed the boot flag.  I then Installed XPSP3.  I got: 
Boots to "grub rescue>"

I have tried the new Ubuntu Security install with Boot Repair, Fixmbr, bootcfg /rebuild, have re-reformatted and re-installed and am now completely stumped.  I have prob booted Live CD and WIN XP cds 25 times - it's been hours and hours!

Still boots to "grub rescue>"

Recap - I have sda and sdb.  
sda has volume one, NTFS, formatted empty. Volume 2 is 160 G of NTFS data. Volume 3 is ext4 formatted empty and Volume 4 is a 3 gig Linux swap.  
sdb is 2 NTFS volumes with data and one ext 4 with only my old 45 Gigs of data in the old HOME dir (everything else there from old Ubuntu Lucid there was sudoed away).

This is a with NEW install of both WinXPSP3 AND Ubuntu Lucid 10.04.3!  I just can't get rid of GRUB2 to boot into Windows! 

I have tried a number of ideas from many sites.  Because of the data on some volumes, I can't wipe either disk completely.  Shouldn't removing the boot flag AND formatting the volume 1 on sda clear EVERYTHING?

Please help...  Thanks!

---

### Post by drs305 on 2011-08-10
The Windows experts will be along shortly I expect. In the meantime a couple of thoughts.

First, are you sure which drive your system is booting from. You can check by entering the BIOS setup during boot and checking the boot order. The MBR of the drive that the BIOS is using is the one that must be cleared. Note that it may not be the one Ubuntu was installed on.

Moving/deleting the boot flag, which Ubuntu doesn't use, won't affect Grub information written to the MBR. Neither will a general formatting of a partition.

I would have expected the fixmbr procedure to work, *if it was used on the correct drive* but I'll leave that for the Windows gurus.

You may save some time by downloading/extracting/running the boot info script and posting the contents of RESULTS.txt, which may show us what is happening.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

You can use lilo, if the Windows boot files are intact, to point to Windows. The boot flag must be present and point to your Windows boot folder. If the Windows boot flag is not on sd**a**, change it in the command below as well. Disregard the messages saying you need to complete the lilo installation. Just run the two commands and reboot.
```
sudo apt-get install lilo
sudo lilo -M /dev/sd**a** mbr
```

---

### Post by emarkay on 2011-08-10
Will fire up the machine and get bootinfoscript on it.

the BIOS boot order...  I did mess with that to try one suggestion (boot from CD first) and it is still CDROM, USB-HDD (none installed) and then HDD-1.    There is a HDD-0, let me try that and see.

SOB, that's better - but now I have 3 Win installs listed one from bootconfig /rebuild. Need to fix that... 

Strange - I don't recall changing the disk number selected in BIOS.  Still at least I have moved forward one step...

Thanks - I am just going to reinstall Win again and see...

Gimme a half hour, then I'll reboot. Then another half hour to load Lucid, and then let's see if I get good booting..    A typo in the BIOS...  that's a new one to me...

Still, since MBR' ing and Formatting and all that didn't "kill" grub, Where in the heck was that data???

---

### Post by drs305 on 2011-08-10
> **emarkay said:**
> Will fire up the machine and get bootinfoscript on ot.

the BIOS boot order...  I did mess with that to try one suggestion (boot from CD first) and it is still CDROM, USB-HDD (none installed) and then HDD-1.    There is a HDD-0, let me try that and see.

I also added an option to install lilo and rewrite the MBR via that method, which you may not have seen since we were 'simul-posting'. But check the boot order first as you don't want to overwrite a working Windows OS if it's just booting the wrong drive first.

---

### Post by westie457 on 2011-08-10
> **emarkay said:**
> I installed a new hard disk (sda), the other existing (sdb) had Ubnutu.  I needed a clean Win XPSP3 install on the PC, so I used GParted to reformat the Ubuntu volume (empty, even sudoed away the Lost and Found dir) and also reformatted first volume on sda to NTFS, and I also removed the boot flag.  I then Installed XPSP3.  I got: 
Boots to "grub rescue>"

I have tried the new Ubuntu Security install with Boot Repair, Fixmbr, bootcfg /rebuild, have re-reformatted and re-installed and am now completely stumped.  I have prob booted Live CD and WIN XP cds 25 times - it's been hours and hours!

Still boots to "grub rescue>"

Recap - I have sda and sdb.  
sda has volume one, NTFS, formatted empty. Volume 2 is 160 G of NTFS data. Volume 3 is ext4 formatted empty and Volume 4 is a 3 gig Linux swap.  
sdb is 2 NTFS volumes with data and one ext 4 with only my old 45 Gigs of data in the old HOME dir (everything else there from old Ubuntu Lucid there was sudoed away).

This is a with NEW install of both WinXPSP3 AND Ubuntu Lucid 10.04.3!  I just can't get rid of GRUB2 to boot into Windows! 

I have tried a number of ideas from many sites.  Because of the data on some volumes, I can't wipe either disk completely.  Shouldn't removing the boot flag AND formatting the volume 1 on sda clear EVERYTHING?

Please help...  Thanks!

Hi.
Unless somebody has a better idea my suggestions to you are 
1 Completely purge Grub from your system using this link. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) 
and rebuilding the XP mbr with the Xp install disc.

2 If that does not work move any files in the data partition to a safe place using a LiveCD. Once that is done fire up Gparted and go to Device > Create New Partition Table. This will effectively wipe the drive of all information. Leave the drive unformatted.
Boot into the XP install disc and use XP's formatting tool to format the drive. Cannot remember if it takes the whole drive or if you can specify how much space you want. Continue with the clean install. 
This should by now have gotten rid of Grub and you can boot into Windows.

All that remains now is to repartition your hard drive and reinstall the distro of your choice. The following list of directions is what I would do. It is not perfect however it is good enough for most people.
> This is what I would do and your choice is to agree or disagree.

1 Boot into Windows and Defrag the C:\ drive at least twice to force Windows into as small a space as possible.

2 Go to disc management and shrink C:\ by as much as Windows allows. Remember that windows is greedy and wants more space than it needs. Leave the free space unallocated for now. 

3 Boot into a Live desktop and run Gparted. In Gparted select the Windows and then move/resize. Shrink this by as much as you want but leaving Windows with enough space. Click okay and Apply. You will now have a lot of free space (unallocated). Again leave this as it is for now.

4 Reboot into Windows. It should immediately tell you your hard drive needs to be checked for errors. Allow this to go ahead and let it finish (better to do this now than later when real problems can occur). And let it finish booting.

5 Restart the computer into the LiveCD and select install. Set a few options relevant to your location and at the where to install screen select something else. You are choosing where to install.

6 In the partitioning window Select the unallocated space choose how large you want his to be; 25000-30000 MB is a good size _25-30GB).Click the first box and select EXT4, then mark the little box to format and then click Use As, select /.

7 Repeat step 6 selecting the remaining space (apart from a size that is equal to the amount of RAM in your computer. This small partition will be your Swap) using this as an EXT4 partition called /home. Remember to mark format.

8 At the bottom of this window is a section for where to install Grub. Make sure Grub goes to the MBR of the drive (the manufacturers name will be here correctly identifying the hard drive.

9 Click Finish and then Apply. The Install goes ahead. If any windows open for where to install Grub you can now accept the defaults.

10 Reboot into your dual-booting computer.

---

### Post by emarkay on 2011-08-10
After I get a good reboot on Win, I'll mark  this Solved...  

I am so grateful for your suggestion, and also so angry that I discounted verifying the BIOS settings - that suggestion showed up in about 50% of the online postings.  
And I have been computing since DOS days. Where's my "Kick Me" sign and Dunce Cap?  

Gimme 28 minutes while I reload again - may as well again start from scratch.

Thanks again!

---

### Post by emarkay on 2011-08-10
> **westie457 said:**
> Hi.
Unless somebody has a better idea my suggestions to you are 
1 Completely purge Grub from your system using this link. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) 
and rebuilding the XP mbr with the Xp install disc.
2 If that does not work move any files in the data partition to a safe place using a LiveCD. Once that is done fire up Gparted and go to Device > Create New Partition Table. This will effectively wipe the drive of all information. Leave the drive unformatted.
Boot into the XP install disc and use XP's formatting tool to format the drive. Cannot remember if it takes the whole drive or if you can specify how much space you want. Continue with the clean install. 
This should by now have gotten rid of Grub and you can boot into Windows.

That was one of the pages I had been to, over the course of today.  Looks like nothing would have helped cause it somehow was getting boot data on  HDD-1 and it should have been HDD-0...  still waiting to confirm.

THANKS, too!

---

### Post by oldfred on 2011-08-10
If you have multiple drives and/or multiple installs the boot script is the best thing around as it tells where everything is at. You do not have to be an expert at debugging boot issues to use boot script just to see what is where. I also use it just to document where everything is at, just in case of a major melt down.

Also to understand Windows booting and some MBR booting in general. Grub does not use PBR - partition boot sector.
You do not need to read entire article, just pictures to start with:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by westie457 on 2011-08-10
> **emarkay said:**
> That was one of the pages I had been to, over the course of today.  Looks like nothing would have helped cause it somehow was getting boot data on  HDD-1 and it should have been HDD-0...  still waiting to confirm.

THANKS, too!

No problem. drs305 got in before me again, my slow typing speed, so did not find out until I had finished writing war and peace from memory. :D

Should also have suggested the use of a SuperGrub2 disc. That might have given more info on what was looking where.

---

### Post by emarkay on 2011-08-10
Thanks again - I got Windows!  (Ugh, not like I am ever going to use it - it's just there as a legacy app...)

Now to activate, configure, secure and then forgetaboutdit, and then to install Lucid...

THANK YOU ALL again!

---

