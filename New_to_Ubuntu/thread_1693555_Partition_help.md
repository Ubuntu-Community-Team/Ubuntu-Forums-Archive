---
title: "Partition help"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by gredawarha on 2011-02-23
Hello all

I have just purchased a samsung q330, it has win 7 installed but I want to dual boot.

when running gparted it shows three ntfs partitions, one is the recovery which I am happy to get rid of, the other large partition is win 7 but there is also a small partition (ntfs) named system.  I am unsure what this is and don't want to remove it in case it prevents win7 from booting.

However with two ntfs partitions  Idont see how I can have my preferred ubuntu setup of three partitions, /root, /home and SWAP as this will exceed the maximum of 4 partitions.

I only want swap so that when I shut the laptop lid it suspends/hibernates.

Any ideas how I might get round this.

P.S.  I have asked on another forum if anyone can identify the smaller ntfs partition too.

Thanks

---

### Post by Hedgehog1 on 2011-02-23
gredawarha,

Congratulations on the new hardware.

Couple of things:

1) Please create a recovery/repair CD and a set of System image disks (or even 2 sets) in case you need to recover the Win7 later.  Don't skip this step before you start changing partitions.

2) You can indeed get the number of partitions you want - that is because a single 'extended' partition is created, and inside that partition you can then make 3 more (Swap, OS and Home).

This image show extended being used for a windows dual install; it demonstrates the concept:
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/2770303.png?767[/IMG]

Oh - that tiny-tiny little partition is the boot partition.  You want that - honest.

:KS

---

### Post by gredawarha on 2011-02-23
Thanks for the reply.  Do you have any recomended sites that might guide me in doing this.  How the hard drive is partitioned at the moment is as follows:

20gb unallocated space
100mb ntfs SYSTEM
45gb ntfs WIN7
450gb unallocated space

---

### Post by Ben Page on 2011-02-23
Windows 7 makes a little 100MB partition for essential system files by default, like bootloader, autoexec, ini files etc. If you delete it, you will render Windows unusable. You can make as many partitions as you like just leave those two (100MB and Windows 7) partitions alone. And be sure to install GRUB on the whole disk, not into a partition, otherwise Ubuntu won't boot.

---

### Post by gredawarha on 2011-02-23
Okay, I shall not be deleting the small partition, thanks for the heads up!

So can I end up with 

ntfs SYSTEM
ntfs WIN7
ext4 /
ext4 /home
swap

or am I goping to have to live without swap?

---

### Post by Quackers on 2011-02-23
Are you intending to install Ubuntu to the 20GB unallocated space, or are you intending to resize the main Windows partition to create space for Ubuntu?

---

### Post by gredawarha on 2011-02-23
Hi Quackers

What I would like is a scenario where I have the following:

ntfs SYSTEM (already in situ)
ntfs WIN7 (already in situ)
ext4 /root 15gb 
SWAP 4gb 
ext4 /home remaining space

THe exact figures do not need to be exact, WIN7 only exists so that I can play football manager.  I need a sensible sized root partition for my ubuntu install and 4gb of SWAP so that I can close the lid of my laptop and suspend/hibernate.  I have chosen 4gb of swap to equal the 4gb of RAM.  The remaining space is for my /home.

---

### Post by Quackers on 2011-02-23
What you want is achievable. I would ask one more thing. Your unallocated space is listed first in your earlier post. Is that where the unallocated space is situated on the drive, at the beginning? This could matter later.

---

### Post by TopgunB on 2011-02-23
I had the exact same struggle a few weeks ago and eventually decided to do an installation using Wubi and it has been great. Get the Ubuntu ISO file from the website and the Wubi file which is 1.5 Mb and put them both into a directory inside Win 7. Click on Wubi and it installs Ubuntu seemlessly. when you boot up you are given a choice of booting into Win 7 or Ubuntu. If you do nothing it will automatically boot to Win 7. You do not have to partition your disk at all, Wubi does it. If you want to later uninstall you can do it through Add/Remove under Win 7. If you partition and later try and un-install Ubuntu it is a HUGE mission.
My Ubuntu runs beautifully in this mode and it is very easy to do.

---

### Post by gredawarha on 2011-02-23
Hi TopgunB  

I appreciate your comments however I am aware of WUBI and it is not for me.  I like to think of myself as a fairly cometent Ubuntu user however having used VIsta before I never needed so many partitions.

Previously I have had a set up such as this:

Vista
/
/home
SWAP

with WIN7 it seems to add a small partition which means I need 5 partitions which is not allowed.  THis is where i am confused.

---

### Post by gredawarha on 2011-02-23
Okay I think I understand the concept of extended partitions having read this:

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

My next question though is can I reclaim the 20gb at the fron of my hard drive?

---

### Post by Quackers on 2011-02-23
You won't need to delete the recovery partition.
You can boot Windows, defragment the C: partition (maybe even twice) then go into disk management and right-click on the C: partition and select "shrink". You need to enter the amount of shrinkage you want, then click OK. The job will take only a few seconds.
At the end of it you will have an unallocated space equal to the amount of shrinkage that you chose. If that space happens to be next to your previously existing unallocated space, it will become one area of unallocated space of 20GB plus your shrinkage.
Then you can reboot Windows at least twice, to make sure Windows is happy about the shrinkage.
Then you can boot from the live cd, selecting "try Ubuntu" and when the desktop loads go to System > Admin > gparted.
When it has scanned the hard drive for partitions you can right click on the unallocated space and select "new", then in the new box which opens up in the right side click on the "create as" box and select "extended partiton" then click Add. A new extended partition will then be created. When done, click on that new partition and select "new" again and create your partitions, one by one, as LOGICAL partitions (NOT primary) in the sizes of your choice. 
This extended partition can have as many logical partitions as you want.

---

### Post by gredawarha on 2011-02-23
Hi Quackers

Problem is when I load GParted at the moment I have the following:

20gb unallocated space
100mb ntfs SYSTEM
45gb ntfs WIN7
450gb unallocated space

I understadn now that I can create the extended partition in 450gb space but surely that will leave the 20gb as it is at the front of the hard drive not the end?

---

### Post by Quackers on 2011-02-23
That's why I asked where it was. Sometimes they lie about where bits are :-)
I misread your existing partitions. I thought that the 450GB unallocated space was a Windows partition. My mistake.
Yes, you can indeed create an extended partition that encompasses all of the unallocated 450GB, then create as many logical partitions as you want to, inside it.
Am I to assume that you already deleted the recovery partition, and that resulted in the 20GB unallocated space at the start of the drive?
If so, you only have 2 primary partitions now, so a third primary partition could be created in that space - an Ubuntu root partition, for instance.

If you intend using hibernation, your swap partition should be slightly larger than the amount of ram you have installed - maybe 4.5GB

Do you understand the mount points required for the individual partitions. These are needed at the installation stage.

---

### Post by gredawarha on 2011-02-23
Hi Quackers

Yes you are right I deleted the recovery partition, this resulted in the 20gb partition at the front of the disc.

So if I have understood you correctly I could create the following

20gb / (primary)
ntfs System (primary)
ntfs Win 7 (primary)
Extended partition 450gb

And within the extended partition create a swap are of say 5gb and the rest as /home.

Thanks

---

### Post by Quackers on 2011-02-23
Yes, apart from not needing to create the 2 NTFS partitions. They are already there aren't they?

---

### Post by gredawarha on 2011-02-23
Yes, the ntfs partitions are existing.  I am at work at the moment but will try it tonight, will post back then.

Thanks again.

---

### Post by srs5694 on 2011-02-23
The 20 GB recovery partition you deleted probably held the equivalent of your installation CDs/DVDs. By deleting it, you've guaranteed that, if and when you need to re-install Windows, you'll need to either go to the manufacturer and spend money to get a set of recovery DVDs or go to a store and buy a retail version of Windows.

Most (all?) new Windows computers include a utility to create a set of recovery DVDs from the partition you've deleted. Thus, if you haven't already used this tool, I recommend you use TestDisk to recover your recovery partition, then locate this utility in Windows. Using this utility, create the DVD set that the manufacturer was so incredibly cheap that they didn't bother to include with the computer. (I recommend you write them a letter, with a cc: to Microsoft; they'll keep being cheaper and cheaper unless and until enough people complain.) Once this is done, you can delete the partition again and still have the tools to recover your computer should the need arise.

More generally, you can create mutliple Linux partitions in your two free spaces. 20 GB is a good size for a Linux root (/) filesystem, so you could create that there (as a primary partition) and then put everything else in logical partitions at the end of the disk. This will work, and it's the safest way to go; however, the problem is that you'll end up with longer-than-desirable disk seeks in Linux, since the disk head will end up seeking between the Linux root (/) and /home partitions, which will have the Windows partitions between them. You can improve Linux performance by moving the Windows partitions so that you've got one single block of free disk space for Linux; however, this runs the risk of rendering Windows unbootable. The Windows disk utility is much more likely to be able to pull this off without problems than is GParted or any other Linux tool, so I recommend you do this from Windows, if at all. I don't recommend you even attempt it unless you've created that recovery DVD set; if it fails, you'll need the recovery DVDs to restore Windows to the computer. If you've got important data on the Windows partition, back it up before attempting to move or resize the Windows partition.

One more point: I strongly recommend against accessing the Windows C: partition from Linux, at least on a regular basis and in read/write mode. If you want to share data between Windows and Linux, I recommend you create a separate NTFS data exchange partition. The reason for this is that Linux doesn't understand Windows' filesystem security features, so it's easy to accidentally damage a Windows installation from Linux. Furthermore, although the NTFS-3g driver that Ubuntu uses seems to be fairly reliable based on anecdotal reports, I find it hard to believe that it's as reliable as or more reliable than Microsoft's own NTFS implementation. Thus, it's possible that Ubuntu will mess up any NTFS partition it accesses, although it's hard to assign a probability to this possibility. The conclusion from both of these reasons is that it's unwise to access the Windows C: partition from Linux any more than is necessary. If you create a separate shared-data partition, you at least won't accidentally trash your Windows installation if you make a mistake when managing your files on that partition.

---

### Post by gredawarha on 2011-02-23
Hi all

I now have dual boot Win7 and Ubuntu just as i wanted it.  Thanks to all

---

