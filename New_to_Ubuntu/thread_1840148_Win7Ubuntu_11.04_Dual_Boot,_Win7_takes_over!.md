---
title: "Win7/Ubuntu 11.04 Dual Boot, Win7 takes over!"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by language4u on 2011-09-07
Hi - I'm *just* starting out with Ubuntu and very gung-ho, but trying to setup Win7/Ubuntu 11.04 dual boots on several machines. Most are successful but one is giving me problems. This machine has two HDDs. Here's what I did:

(1) put 4 partitions on one HDD, left other unpartitioned
(2) installed Win7 on primary partition of first HDD
(3) installed Ubuntu 11.04 via CDROM on second (logical) partition of first HDD, and made a small swap file in the 3rd partition and made the 4th partition \home (probably, I shouldn't have bothered with this, but anyway).

All seemed to go fine, but when I rebooted without the CD I don't get grub - Win7 just starts right up.

I think I probably put grub in the wrong place, but I don't know how I did this. Can anyone help?

Many thanks in advance for any help you can offer!!!

---

### Post by MG&amp;TL on 2011-09-07
Probably next time, choose 'install alongside windows 7' on the partition options.

I think the problem is that BIOS boots straight to the first HD, and never sees GRUB in the first place, only the windows MBR. I'm not sure how to get around this, part from the aforementioned option. If Ubuntu is on one HD, and windows is on the other, you could try making the linux HD the primary one (swap the cables around.) Grub should then boot, and you should be able to choose then.

Btw, word of warning, don't use windows recovery mode too lavishly, for some reason when I did that, it ate my linux partition, so it booted to grub rescue because grub couldn't find a linux partition as such. Windows eats Linux. (and Mac OS, I guess)

---

### Post by language4u on 2011-09-07
Thanks for the fast reply. 

So if I understand you right, if I go ahead and re-install Ubuntu choosing the "alongside" option, I should get more guidance in partitioning sensibly and the boot loader will automatically go in the right place?

Thanks again!!

---

### Post by mastablasta on 2011-09-07
alongside option will basically auto partition the empty disk for Ubuntu and will put the grub in the first part of disk.
 
when you set up your Ubutnu partitions, you probably didn't specify where the grub should be or you specified wrong.
 
for more info on what happened and how to fix it it would be good if you could post the results.txt file that is provided by bootinfoscript found here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
i think you might be able to simply move/install the grub to first part of disk.
 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (check chapter 12: [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2))
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Mark Phelps on 2011-09-07
If you use the alongside option, make sure you do NOT allow the Ubuntu installer to shrink the Win7 OS partition.  Doing so risks corrupting Win7 and rendering it unbootable.

Better approach would be to use the Win7 Disk Utility function to shrink the Win7 OS partition.  Then, boot into it a couple of times to allow it to do any filesystem adjustments.  Leave the new space unallocated.

THEN, before you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will allow you to repair the Win7 Boot Loader, should it become damaged later.

---

### Post by language4u on 2011-09-07
mastablasta, thanks for the great reply!

I've done what you said and attached the results.txt file here.

From what I can see you're right, there's a mismatch in where grub and the Win7 MBR are located. 

It's a little bit weird, but there's an unusable HDD in the tower (don't know what's wrong with it) which seems to be getting read as sda1, and it looks like this is where grub is. Meanwhile it looks to me like Win7 is booting from sdb2, but I'm confused where it says "Windows is installed in the MBR of /dev/sdc."

So first question: should I not worry about this and assume that GRUB needs to live in sdb1? 

And if so, second question: should I reinstall so that everything is living in the right place, or just move the GRUB folder into the same directory where Win7's "Boot" folder is living?

Sorry for the naive questions - obviously, I'm really new at this and want to get it right!

Many thanks!!

---

### Post by oldfred on 2011-09-07
Grub2 has several parts, most is installed in your /boot folder in your Ubuntu install. You install the grub2 boot loader to the MBR of a drive to boot. Since you have multiple drives you can have different installs in each drive.

If you change BIOS to boot sda or use one time boot key at BIOS screen (f12 on my system) to choose sda, does it then boot? You have two 500GB drive and in BIOS they may look identical (there will be a serial # difference). With my system I have 2 160GB drives and initially had to just try booting one or the other until I realized BIOS always saw them in the same order.

If you can boot you can just reinstall the grub2 boot loader to the MBR of sdb.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Did you buy a system with a 1TB drive and got two 500GB drives? You then also seem to have a 320GB drive.

---

### Post by language4u on 2011-09-07
Thanks mastablasta, oldfred and others - I just went ahead and reinstalled, repartitioned so that sdb had a Win7 partition, a 10Gb swap partition and an Ubuntu partition, then had it install GRUB to sdb (not specifying a partition). I've just rebooted and I can get into both Win7 and Ubuntu just fine. Hooray!

So I guess that the bottom line is, when selecting "something else" in an Ubuntu install when you've got multiple drives, first run the bootscript via an Ubuntu LiveCD to make sure you know where Win7 is booting from, then select that drive for GRUB to live in. 

Thanks again for the great help! Ubuntu rules!

---

