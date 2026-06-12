---
title: "Ubuntu 8.10 live CD boots to busybox"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by cojon on 2009-02-07
I sincerely hope I am doing this post correctly. This must be the most confusing two weeks I have ever experienced as every term is new and definitions are not often forthcoming. I am  attempting to triple boot Ubunto, Vista, and XP. 

The problem NOW, is that the Ubuntu 8.10 live CD boots to busy box v1.0.2 (I think that's the v number) with the prompt showing > Initramfs_

The CD previously booted correctly, but I think I installed Ubuntu incorrectly by placing Grub on / and not /home. Just understanding the partition requirements was an exercise in absolute frustration. A bit like learning Chinese without a book.

Here is some additional info. Apologies, I don't know what is needed or what is not.

I have NEVER used Ubuntu 8.10 before, but I have 30 years computer experience and can deal with anything IBM/MS. Beyond that I'm like a new child. I'm 67, disabled and have some memory difficulties, so please, if you can, be complete and define  terms I would not be expected to know, or point me to a site with definations. Thanks. 

I am attempting to do a triple boot with Vista, XP, and Ububtu, and so far without success. I can install Ubuntu and it will boot using Grub on HD0,0, but I have to use Dell's utility to choose the drive to boot from. Otherwise, only Vista'a multiboot menu shows up. I presume Grub is ineffective because it is  installed on HD0,0 and it should be on HD0.1 or the /home partition. That or my SATA/IDE mix is creating the problem. Am I correct?

I am fortunate to have three hard drives; one for each OS. 

Ununtu is on HD0, a 40 GB IDE partitioned with / at 8 GB on partition 0 (a primary), /home  at 28 GB on partition 1(logical) and a 1.6 GB (logical) partition 2 for the swap partition. All are formatted Ext3. The machine is a Dell 8300, Pentium 4 2.4 GHz, 4 GB RAM, Nvida 6200 video card, single 22" widescreen TFT monitor. 

XP is on HD1,0 a 250 GB IDE with two partitions, Vista is on HD2 a 750 GB SATA drive with five partitions. Both formatted NTFS.

I have attempted about everything I can find to get a clean triple boot using the grub menu. I hear it is a robust and effective bootloader, and I like the options of a command line menu. I did get all three OS's on the boot menu by editing /grub/menu.lst and they were functional but I had to boot via F12, Dell's device to select the drive to boot from. From there, everything worked but Vista and XP only jumped to the Vista boot menu requiring yet another selection before they went further. 

I added drive mapping to the Vista loader as suggested somewhere (HD0 HD1) (HD1 HD0)but with no apparent difference. The Vista boot menu still came up alone. Grub was only functional when I booted from that particular drive--an IDE with Grub on HD0,0, by using Dells boot utility invoked by F12. 

Next, I attempted to use EasyBCD, and that provided no solution. I now realize that having Grub on HD0,0 was a problem for EasyBCD--it couldn't find Grub, which really needs to be on HD0,1 where EasyBCD will find it.

Lastly, I simply removed Ubuntu as there was little setup work in the installation and then I attempted to remove Grub from HD0,so I could reinstall Grub on the correct partition--so EasyBCD could find it. I think I finally decided that the mix of IDE (PATA)and SATA drives was a rather serious problem as they boot differently with the IDE using the BIOS while the SATA doesn't. 

Finally, using a small MBR utility I downloaded called MBRfix I tried to wipe Grub from the MBR of HD0. The command (from a DOS window in Vista)...> mbrfix /drive 0 fixmbr /vista /yes produced nothing that altered much. Grub still appears to happily inhabit HD0,0 and the live CD still boots quite reliably to busy box. Whatever that thing is.

I just had a thought. Perhaps a DOS command to write the Vista MBR may be compromised or thwarted if issued from within Vista. Yet I didn't receive any errorcodes so I assume it was successful. I will make another attempt to restore the Vista MBR, but this time in safe mode. 

Please, if you have information that may help, do offer it even if little more than to say I'm on the correct track. I do love a challenge, but learning Ubuntu is extremely difficult when I get undefined words that mean little more to me than the following might to you... 

"Drop the big Bruce here and Y the Danforth off at a forty five. Set it on fifty feet of triple B with a shackle and lay it on a forty five to the main's set at 240 true. Set 'em real hard and drop a couple o' kellets leaving a fathom for lift. Swinging's OK, but I don't want to drag or pull out in a force 10 low." 

Sailing lingo. I'm an old captain so I know it, but to most it's pure Greek. That's how I feel with Ubuntu words, so please help me with some clues or short definitions. Thanks so much for your patience.

---

### Post by SteveDee on 2009-02-07
I think you've chosen a difficult route to gain familiarity with 'buntu. But if you want to continue with your triple boot approach, I suggest you take a look at Super Grub as this is a great utility for sorting out problems with Grub, MBR & Windows.

Check this out: [http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

---

### Post by cojon on 2009-02-07
> **SteveDee said:**
> I think you've chosen a difficult route to gain familiarity with 'buntu. But if you want to continue with your triple boot approach, I suggest you take a look at Super Grub as this is a great utility for sorting out problems with Grub, MBR & Windows.

Check this out: [http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

I will look at SuperGrub. Thank you.

As far as your consideration of triple booting as a difficult route, what might you suggest? I'm using a dual boot system now, and if you read my post carefully, you will notice that I can and have accomplished a triple boot, but prefer having all OS's boot cleanly from ONE single menu, not requiring both menus. I guess I'm fussy and want it my way. The problem seems to stem from having a SATA-PATA mix of disks on the same machine. The SATA doesn't use the BIOS to boot as do the IDE's and perhaps that's the problem. I don't know how Linux (Ubuntu) handles things of this nature and so goes the confusion.

If I am correct, the current difficulty seems to be in removing Grub from the HD0,0 MBR, and placing it on the HD0,1 /home partition where EasyBCD can locate it. Then all would work. The triple booting has not been overly difficult, just took a lot of time find clues on the language.

As to the triple boot against whatever you might be suggesting, I really am not interested in removing other systems in favor of the new guy on my desk. He will just have to get along with everyone already in residence. Nor do I think another computer is justified just for Ubuntu. So what would you do? I don't believe there exists another reasonable approach unless I install Ubuntu into Windows, and I really don't think that is the solution, nor is continuously booting from the live CD. I'm open to suggestions, if there is something I have not considered. Personally however, I don't believe the concept or installation of a triple boot is particularly daunting. Killing that MBR, apparently is however. Nothing seems to work.  

Thanks for your suggestion, and I will investigate SuperGrub with some intensity. The way things have been going I doubt this will be easy, but solution's do often present themselves as one pushes forward and I suspect I will find a trail through this jungle eventually. An experienced native guide would be oh so helpful, and certainly faster however.

Thanks...

---

### Post by cojon on 2009-02-07
> **SteveDee said:**
> I think you've chosen a difficult route to gain familiarity with 'buntu. But if you want to continue with your triple boot approach, I suggest you take a look at Super Grub as this is a great utility for sorting out problems with Grub, MBR & Windows.

Check this out: [http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

I will look at SuperGrub. Thank you.

As far as your consideration of triple booting as a difficult route, what might you suggest? I'm using a dual boot system now, and if you read my post carefully, you will notice that I can and have accomplished a triple boot, but prefer having all OS's boot cleanly from ONE single menu, not requiring both menus. I guess I'm fussy and want it my way. The problem seems to stem from having a SATA-PATA mix of disks on the same machine. The SATA doesn't use the BIOS to boot as do the IDE's and perhaps that's the problem. I don't know how Linux (Ubuntu) handles things of this nature and so goes the confusion.

If I am correct, the current difficulty seems to be in removing Grub from the HD0,0 MBR, and placing it on the HD0,1 /home partition where EasyBCD can locate it. Then all would work. The triple booting has not been overly difficult, just took a lot of time find clues on the language.

As to the triple boot against whatever you might be suggesting, I really am not interested in removing other systems in favor of the new guy on my desk. He will just have to get along with everyone already in residence. Nor do I think another computer is justified just for Ubuntu. So what would you do? I don't believe there exists another reasonable approach unless I install Ubuntu into Windows, and I really don't think that is the solution, nor is continuously booting from the live CD. I'm open to suggestions, if there is something I have not considered. Personally however, I don't believe the concept or installation of a triple boot is particularly daunting. Killing that MBR, apparently is however. Nothing seems to work.  

Thanks for your suggestion, and I will investigate SuperGrub with some intensity. The way things have been going I doubt this will be easy, but solution's do often present themselves as one pushes forward and I suspect I will find a trail through this jungle eventually. An experienced native guide would be oh so helpful, and certainly faster however.

Thanks...

---

### Post by SteveDee on 2009-02-08
I was not trying to imply that your (triple boot) approach was unreasonable, so sorry if I gave that impression.

People use 'buntu (and computers in general) for a range of different reasons, and some just want to explore the technology.

I guess you wouldn't be happy booting & running Ubuntu from a memory stick, so I hope Super Grub will provide you with an answer.

---

### Post by cojon on 2009-02-09
Thanks SteveDee, I didn't take it that way either. I just don't have any solutions myself and am at a loss for directions to take. I did consider using the live CD, but recall, it doesn't boot. It just goes to busybox and I haven't a clue about that thing. All the info I find seems to just bang heads with the other one. I'm getting mnowhere. I did put Ubuntu 7.04 on to see if that would work. I picked that up some time ago but the road to Linux, as I'm sure you are well aware, is filled with confusion and a lack of clear documentation. 

I have several books, but they are poorly written and both assume you both know the language as well as where to apply the commands they are discussing. They are about a five asprin approach to learning.

Oh well. Maybe all the people on this forum with similar difficulties and the same misunderstanding will get something and I will spot it--if I can find it. Took me a week to figure out how to post something. Must be the initiation... No problem. I'm in for the long haul if I could just get started.

---

