---
title: "Some quirks on successful installations"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Andy06 on 2008-12-30
So I've been on a marathon run installing Ubuntu 8.10 on 12 computers. All successful (mostly :)), but I do have some newbie questions about quirks in some of the installations. All of the computers (all notebooks) had pretty much the same Hard disk setup, a C: drive with either Windows XP or Vista, an F: drive for Personal files (Docs, Pics, Music, Videos, Downloads) and some of them had recovery partitions as well (usually D: ), with E: being the optical drive.

So here go the questions:

1) Whenever the C:/ (Windows partition) was not too big (<40 GB), I needed Gparted or Perfect Disk to shrink the partition and create more space since the in built windows tools cannot move system files and MFTs. However, both Gparted and Perfect disk seem to mess up the MFT a bit when they defragment/move it. Basically the entire hard disk could not be read for a while with customised settings losing their configuration if they had to read it off the hard disk. Even firefox stopped saving anything to cache. I initially though this could be because of the re-installation of the hard disk drivers (which windows reloaded everytime I messed too much with a non windows partition program), but later realised it had to do with the MFT. The defragging, resizing and moving of the MFT probably left orphaned entries and screwed the locations. Curiously however, this problem rectified itself in all but one computer. All Vista computers resolved the issue by themselves in 4-5 restarts whereas 1 XP computer is still not able to read some info (firefox settings, gadget customisation, wallpapers, customised icons, other personal settings etc) off C: drive. Any ideas on whether this problem really has to do with the MFT? 

2) Can linux create more than 4 primary partitions on a disk? Most comp had 3 primaries (C:, D:, F: ) and then I created an extended partition in which linux could create it's own logical partitions. However after installation, the 3 logical partitions that linux created show up as primary partitions in vista's disk management tool, so now I have 6 "primary" partitions. Is this possible? Also why does Linux create 3 partitions, one if "/", another is "swap", what's the third one for? [I've attached a screenshot of the set up at the end of the post]
Note that this 3rd partition is NTFS here, so linux did not reformat it to ext3.

3) The new ubuntu installations are a bit slower than the live USB systems I tried. Is this possible or is something wrong? Is it perhaps because the full installation is on 5400 rpm HDDs whereas the Live USB were running from flash memory and RAM? The new installations sometimes do speed up considerably which makes me thing something is going on in the background that I am not aware of. 

4) I checked Indexing and its not running (the enable indexing check box is unchecked), however on exiting the indexing settings, it says it needs to reindex to apply new settings? Does this mean it will index again in order to STOP indexing??

5) I know people complain about Vista's UAC but in comparison Ubuntu's elevation system is driving me crazy. It pops up for EVERYTHING! I feel Vista is way way more discreet. Is this normal? I do not usually hear complaints from ubuntu users about the elevation so maybe I've configured something wrong? 

6) Is there a way to auto mount internal HD partitions at start up? I have a lot of settings I'd like to share between Vista and Ubuntu and so would prefer to keep them on a shared partition (wallpaper for example), however whenever I restart ubuntu, it loses the configuration since the partition is not mounted automatically. External HDs mount as soon as they are plugged in, so I'm sure there is some way to auto mount internal HD partitions. 

7) For computers with Nvidia cards, I installed the 177 version driver but there seem to be a fair bit of tearing and disappearing of window title bars going on. Would the older 173 version driver be more stable. Ironically, the Intel integrated graphics cards seem to be doing a better job of handling compiz.

8 ) Some external drives have folders to which ubuntu prevents write operation by citing insufficient privileges/permissions, why is this?

9) Lastly, soon after a full install, the update manager comes up with about 225 MB of updates to be downloaded, however I see a lot of redundant stuff in the list such as firefox 3 and totem (not the associated packages with some add on functionality but the basic install package itself), are these updates necessary, shouldn't they auto detect the redundancies?

BTW, I learned during these installs that the safest way to dual boot Vista and Ubuntu is to install GRUB to the "/" partition where the ubuntu file system is and NOT the MBR. This leaves Vista and its MBR bootloader untouched and does not even have the potential to cause any issues. Then install EasyBCD in Vista and use it to add a grub chainloading reference to the vista bootloader (this is an automated 3 steps/click process). This method eliminates any need for menu.lst tweaking and also removes the risk of GRUB messing something up by either not recognising Vista (which I never experienced) or by overwriting the MBR (this did cause problems in some setups). 

Perhaps, the official ubuntu documentation or general advice should include this method instead of the usual GRUB to MBR method. Even the advice to use EasyBCD is sometimes not the best out there as some guides ask you to let GRUB install to the MBR, then fix Vista's bootlader by overwriting GRUB using EasyBCD and THEN modifying Vista's bootloader by manually pulling the GRUB options from ubuntu and then manually editing the menu.lst file [this is the method recommended in the very popular and otherwise excellent step by step dual booting online guides by apcmag.com: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm])

Thank you very very much

---

### Post by LowSky on 2008-12-30
OK WOW that is one long post...

1) you should always defrag a hard drive in WIndows before using shrinking the partition.

2) No OS can create more then 4 primary partitions. Using an Extended Partition to manage logical partitions is what is need regardless, They should show up in Vista as unknown partions if you use EXT file systems

3)Flash and RAM are much faster then hard drives (the slwoest part to any computer is the hard drive)

4) I believe indexing need to run one full scan before it can be effectily turned off.. I am most likely wrong, as I can t find any info. I usually turn it off.

5)This is something that does pop up every once in a while. While Vista is horrible about it, Ubuntu only does it for using admin privaleges. You could turn on the root user and use that for admin task so you dont need to always ask for a password, but I isn't an Ubuntu philosphy to do so.

6)Yes, If they are NTFS you will need NTFS config and  NTFS-3g, they will install to Applications menu

7)177 has some issues, 173 may work better, or use the beta 180 from Nvidia website.

8)These drives assume they are not owned by you, these settings can be changed easily. Also If you dissconnect a drive under Windows incorectly (not safely) this sometimes happens, to fix just boot windows, safely remove and you should be fine)

9)There are actually sercuity updates and bug fixes. Because of the packaging system Ubuntu uses the whole package is downloaded and reinstalled, inst5ead of a small file here of there this allows for less errors to occur from updates like you may see on Windows.

BTW) you could creat a /boot partiton to better manage your boot programs.

---

### Post by Andy06 on 2009-01-01
I know its a long post. But I'll accept answers to any one of the questions as well if its too boring to read fully.:D

---

### Post by Andy06 on 2009-01-01
> 1) you should always defrag a hard drive in WIndows before using shrinking the partition.

I did that, but the windows defragger is very basic and does not defrag large files, system files, pagefiles, hiberfil.sys, MFT and VSS (most of the these I disabled anyway). We have to use either Gparted or Perfectdisk like programs and they both seem to cause the MFT issues mentioned above.

> 2) No OS can create more then 4 primary partitions. Using an Extended Partition to manage logical partitions is what is need regardless, They should show up in Vista as unknown partions if you use EXT file systems

Yea I know you're right but in my attachment in the first post, they show up as primary partitions, probably a bug.

> 3)Flash and RAM are much faster then hard drives (the slwoest part to any computer is the hard drive)

Would running Ubuntu from a very large flash drive (8 or 16 GB) with persistence make more sense then installing it fully on a Hard disk then? I can't think of any shortcomings, I use Live USBs a lot anyway and find theyre far more convenient as they can be re-created any time AND they don't require us to elevate anything, it always seems to be in de facto root.

> BTW) you could creat a /boot partiton to better manage your boot programs. 

Is that for new manual installations or can I still do it? If so, how? Is the third NTFS partition created by Ubuntu in the attachment (first post) a /boot partition,/home or something else.

Thanks a lot for the help

---

### Post by albinootje on 2009-01-01
> **Andy06 said:**
>  3) The new ubuntu installations are a bit slower than the live USB systems I tried. Is this possible or is something wrong? Is it perhaps because the full installation is on 5400 rpm HDDs whereas the Live USB were running from flash memory and RAM? The new installations sometimes do speed up considerably which makes me thing something is going on in the background that I am not aware of. 


5400 rpm disks (in laptops, some old ones had 4200 rpm) are slower then the 7200 ones in normal desktop machines.
RAM memory is really compared to that.
Usb-sticks (not usb-disks) are much faster on usb 2.0 ports than on the old usb 1.x ports, but I'm not sure how they compare to hard disks.
Perhaps it's the combination of reading from usb-stick and "pre-loading" in RAM memory what made it look faster.

Next time, please try to ask one question at a time, and make your posting a little shorter.
It's nice for you that you got all questions answered now, but I think I was not the only one who was about to skip your posting completely.
Just FYI. :)

---

### Post by albinootje on 2009-01-01
> **Andy06 said:**
> I did that, but the windows defragger is very basic and does not defrag large files, system files, pagefiles, hiberfil.sys, MFT and VSS (most of the these I disabled anyway). We have to use either Gparted or Perfectdisk like programs and they both seem to cause the MFT issues mentioned above.

What is MFT ?

And FYI, years ago with W95 and W98 defragging was really needed before the commandline split tool could split the windows disk partition in two. 

But in the last year or so I've hardly seen any problems with resizing a Windows-partition during Ubuntu installations.
Perhaps this is also because hard disks are much bigger now.
So I'd take "always defrag before resizing !!" comments with grains of salt.

> 

Yea I know you're right but in my attachment in the first post, they show up as primary partitions, probably a bug.

Send MS a bug-report ;-)

---

### Post by Andy06 on 2009-01-01
> It's nice for you that you got all questions answered now, but I think I was not the only one who was about to skip your posting completely.

Hehe, yeah I realised that. I will keep it in mind. Its just that I'm installing for people in a college dorm and have been having different issues on different comps, so I thought I'll post them all together........bad idea :)

> What is MFT ?

MFT = Master file table

Windows' list of references for various file locations. A sort of index for your hard drive really

> 
And FYI, years ago with W95 and W98 defragging was really needed before the commandline split tool could split the windows disk partition in two.

But in the last year or so I've hardly seen any problems with resizing a Windows-partition during Ubuntu installations.
Perhaps this is also because hard disks are much bigger now.
So I'd take "always defrag before resizing !!" comments with grains of salt.

I think it's necessary, because the later versions have a lot of "unmovable files". These include the pagefile, hibernation file (both usually around a gig), the MFT (which can be quite fragmented in Vista) and lastly the VSS (volume shadow storage, the restore files, this can be multiple gigs, in fact it is usually more than 20 GB in large hard drives).

A big problem with Vista is that the MFT can only be grown, not shrunk. So once it has grown to say 10 GB (unlikely, but as an example), it does not shrink automatically even if its contents (the actual files and hence the references to those files) are deleted. This "reserved space" within the MFT is then the last thing that the Hard disk writes on...usually after every other byte is used up. So if the Vista installation isnt brand new, a 3rd party defragging/partitiong software is required.

---

### Post by albinootje on 2009-01-01
> **Andy06 said:**
>  I think it's necessary, because the later versions have a lot of "unmovable files". These include the pagefile, hibernation file (both usually around a gig), the MFT (which can be quite fragmented in Vista) and lastly the VSS (volume shadow storage, the restore files, this can be multiple gigs, in fact it is usaully more than 20 GB in large hard drives).

A big problem with Vista is that the MFT can only be grown, not shrunk. So once it has grown to say 10 GB (unlikely, but as an example), it does not shrink automatically even if its contents (the actual files and hence the references to those files) are deleted. This "reserved space" within the MFT is then the last thing that the Hard disk writes on...usually after every other byte is used up. So if the Vista installation isnt brand new, a 3rd party defragging/partitiong software is required.

Why don't you just test it before defragging ?
It might save you quite some time. 

And, if that works, with that knowledge you can help other people safing time.

You can cancel the Ubuntu installation after it would tell you that the resizing can't be done because defragging would be needed.
Make sure to make backups first.
Not likely that your laptop has an empty battery when a power-failure occurs during resizing, but better safe than sorry ;-)

---

