---
title: "Missing Hal.dll, remove XP, consolidate 2 hard drives in one system, can't see parti"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by chipmcd on 2011-03-23
Skill level:
Beginner here. I have few questions that flow together in a way.

How I installed:
I installed Ubuntu 10.04 64bit and Windows XP on one 500gb hard drive by using Gparted from a liveCD to create my partitons.  I installed Windows first, then Ubuntu.  Think it was like 100gb, 100gb and the rest a storage partition.

* Problem 1: *hal.dll error*
I hadn't used XP yet.  When I tried to select it, I got the missing hal.dll error and it said to re-install it.  Tried that and it messed up the Grub (no grub).  Searched for a fix and got the grub to work ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows))  Back into Ubuntu but still no XP.

Question:   There's no repair console option with the XP cd (the method some articles said to used to repair this problem.)  Is there a way to fix the hal.dll problem without it?  Haven't seen one online yet.

* Problem 2: *Can't see some partitions after fixing grub problem*
After fixing, I cannot see a couple of partitions that I used to see from Ubuntu.  One was the Windows XP partition and another is one I used for storage of files.  Nothing important but things that took a long time to do (ripped a bunch of my cds and started to rip my dvds.) Gparted, from a liveCD, showed the partitions but I couldn't get information on either.

Question:   I once saw the windows partition from inside Ubuntu but have not seen it again.  How can I get these to show up again in Ubuntu or at least the storage partition?  I ran that bootinfoscript and got a results.txt file if needed.

* Problem 3: *Uninstall XP from the dual boot on this drive*
If I can't get XP to run again, then I will just get rid of it.

Question:  Is there any downside to just deleting the partition from Gparted?  Also, the disk utility inside system/administration doesn't seem to work after fixing the problem from above.

* Problem 4: *Consolidate 2 hard drives in one computer*
If I can get rid of the Windows XP from this dual boot then I'm thinking of consolidating two separate hard drives into one pc.  I would be adding to this Ubuntu 10.04 hard drive a hard drive that has Windows XP only. Both SATA drives by the way.

Question:  Would I just need to select the Ubuntu hard drive to boot first in the BIOS, then update-grub in Ubuntu to get a dual boot?

Thanks for taking the time to read this post.

---

### Post by oklokl on 2011-03-23
ubuntu only
Master Hard first
Recognition
Manual editing
Must
Setting the boot partition, partition
/ Ext4 generation .. ->os install Space
Expand
+ swap 2G
If you do not

auto ubuntu setting ->
Boot location
You do not know
Boot is in Space 
Encoding installed


Tried to test all versions

4EA Points

Manual
Select
/ -> os

{ [swap Default memory area] Cover the extended partition}

boot Space You first HDD Bios
Hard

+Tip
Clonezilla Backup Program only ext4
ext3 error.. die system

Contrary
xp..
[http://blog.daum.net/goongocompter/94](http://blog.daum.net/goongocompter/94)

[http://www.lug.or.kr/docs/LINUX/others/01-05-5.htm](http://www.lug.or.kr/docs/LINUX/others/01-05-5.htm)
[http://foxtech.tistory.com/2](http://foxtech.tistory.com/2)
[http://2fered.pe.kr/981](http://2fered.pe.kr/981)

[http://www.diskool.com/891190](http://www.diskool.com/891190)
[http://noneway.tistory.com/37](http://noneway.tistory.com/37)

Partition
Principle -_-;;;??
auto install setting
IDE First
sata 2
AHCI
= Constant current
Ubuntu System

---

### Post by crispy_420 on 2011-03-23
You need to decide: dual boot or not. There are pro and cons either way.

Fix Windows:
Well if you have a normal Windows XP disc and not some OEM installer you could try to fix XP as so:
[http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm](http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm)

The recovery console is on the disc. If you would like a permanent recovery console, you can download one through MS and it will appear as a boot option.

Missing Data/Partitions:
It sounds like you may need to be more cautious on install because you may be overwriting partitions.

Remove XP with GParted:
You can remove the XP data but be cautious as to the correct data being deleted. Remove only NTFS (or FAT) partitions and then you can expand Ubuntu to fill the gap or create a data partition.

Dual Harddrives:
There is another option if want to push forward with both. If you have a few extra bucks and an empty 5.25" bay, why not get a removable drive bay and an extra caddy? Makes life easy and all issues mentioned would be gone.

---

### Post by quirks on 2011-03-23
> * Problem 1: hal.dll error

Sorry, I have no idea what was broken nor how to fix this. I have never heard of such an error. It sounds serious. Re-installing Windows XP is probably the easiest/safest way to fix it.

> * Problem 2: Can't see some partitions after fixing grub problem

Unless you explicitly deleted partitions during the re-installation process of Windows, the partitions should still be there. Maybe, Ubuntu simply does not mount them automatically. Can you give me the output of this command:
```
sudo fdisk -l
```
This prints the partition layout. If the partitions are still there, I can show you how to mount them manually.

> * Problem 3: Uninstall XP from the dual boot on this drive
If I can't get XP to run again, then I will just get rid of it.

Question: Is there any downside to just deleting the partition from Gparted?

There is no real downside. The numbering of your partitions will start with 2, but that is just a cosmetic detail. You can even enlarge the neighboring partitions to consume the space of the deleted partition. This may take a couple of hours, though, because GParted will need to move a lot of data on the disk.

> Also, the disk utility inside system/administration doesn't seem to work after fixing the problem from above.

Can you elaborate a little? What does not work? Are there any error messages?

> Question: Would I just need to select the Ubuntu hard drive to boot first in the BIOS, then update-grub in Ubuntu to get a dual boot?

I am positive that it works exactly this way, yes.

> Thanks for taking the time to read this post. 

Thanks for not throwing in the towel.

Let me know, if anything is unclear or if you run into problems.

@oklokl: I don't understand your post. Is this an answer to chipmcd? Would you mind writing full sentences?

---

### Post by tedygram311 on 2011-03-23
> **chipmcd said:**
> 
* Problem 1: *hal.dll error*
I hadn't used XP yet.  When I tried to select it, I got the missing hal.dll error and it said to re-install it.  Tried that and it messed up the Grub (no grub).  Searched for a fix and got the grub to work ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows))  Back into Ubuntu but still no XP.h

Question:   There's no repair console option with the XP cd (the method some articles said to used to repair this problem.)  Is there a way to fix the hal.dll problem without it?  Haven't seen one online yet.


hal.dll I believe is a windows file, I could be wrong about that but you may want to try to repair windows first, then repair ubuntu with a live cd (so that you get grub again)

> 
* Problem 2: *Can't see some partitions after fixing grub problem*
After fixing, I cannot see a couple of partitions that I used to see from Ubuntu.  One was the Windows XP partition and another is one I used for storage of files.  Nothing important but things that took a long time to do (ripped a bunch of my cds and started to rip my dvds.) Gparted, from a liveCD, showed the partitions but I couldn't get information on either.

Question:   I once saw the windows partition from inside Ubuntu but have not seen it again.  How can I get these to show up again in Ubuntu or at least the storage partition?  I ran that bootinfoscript and got a results.txt file if needed.

This is more than likely because the drive is busy.  You may want to try to mount the drive and see what happens:
```

sudo blkid (this will list your partitions by uuid)
mount (uuid)

```NO promises there but it may or may not work.  If it is busy you more than likely tried to set it up so that it would mount automatically and messed up along the way.  My school has a wiki that will guide you on this [https://vtluug.org/wiki/Ubuntu](https://vtluug.org/wiki/Ubuntu). (Moderator I am not sure if it is ok putting this up there I just know where it is and it might be easier for him)

> 
* Problem 3: *Uninstall XP from the dual boot on this drive*
If I can't get XP to run again, then I will just get rid of it.

Question:  Is there any downside to just deleting the partition from Gparted?  Also, the disk utility inside system/administration doesn't seem to work after fixing the problem from above.
No downside aside from not having windows which may be needed if you are in school.  There are some programs that don't have a linux equivilent.

> 
* Problem 4: *Consolidate 2 hard drives in one computer*
If I can get rid of the Windows XP from this dual boot then I'm thinking of consolidating two separate hard drives into one pc.  I would be adding to this Ubuntu 10.04 hard drive a hard drive that has Windows XP only. Both SATA drives by the way.

Question:  Would I just need to select the Ubuntu hard drive to boot first in the BIOS, then update-grub in Ubuntu to get a dual boot?
If you decide to get rid of windows I would put in a live cd to try to back up all of your files from windows possibly onto an external or just move them to your linux partition.  You will be able to see all of them from a live cd.

> 
Thanks for taking the time to read this post.Welcome!

---

### Post by oldfred on 2011-03-23
Missing hal.dll is ususally another boot error, not the missing file. Often as simple as a boot.ini having a bad entry or a chkdsk required.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

You can repair just about everything related to XP from Linux liveCDs including Ubuntu except running chkdsk. And you can use a win7 or Vista repair CD to run chkdsk, and some other repairs for XP.

I like having two drives with different operating systems on each. But windows prefers to be sda or drive 0. (May also be BIOS related.) Ubuntu handles different drives much better.

---

### Post by chipmcd on 2011-03-23
Thanks to everyone who replied. 

@oklokl
thanks for the reply but you got me stumped.  Not really sure what you were trying to say.  I am a noob at this Linux stuff and couldn't quite understand everything.

@crispy_420
Thanks. I tried that link to fix the hal.  When I started up the XP cd, I never got the Repair/recover option (I went to the step in the installation where it asks to select a partition to install; I stopped there.)  It went straight to wanting to install.  It asked to select where XP was to be install (select the partition.)  I exited there not wanting to disrupt anything before trying other methods of restoring the hal.  But upon re-booting, that's when the grub went down and I subsequently had to fix it.  

About the missing partitions - I was able to see them for a while until I tried to do the Windows stuff.  I used Asunder and DVD Shrink under WINE and stored stuff on that big storage partition.  I saw the Windows partition last night before I posted to the forum.  But after rebooting, it was gone, too.

That swappable drive bay sounds like a good idea.

@quirks
At the point where it said to select a partition to install XP on, I stopped there.  I didn't want to re-install anything, just repair.  And like I mentioned before I didn't get the repair option ("R") in the setup.

Here is the output you requested:
******************************Start*************************
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5593    44920832   83  Linux
/dev/sda2            5593       12748    57475431    f  W95 Ext'd (LBA)
/dev/sda3            6376       12748    51191091    e  W95 FAT16 (LBA)
/dev/sda4   *       12749       25496   102398310    7  HPFS/NTFS
/dev/sda5            5593        6375     6284288   82  Linux swap / Solaris

*****************************End****************************

And about the disk utility, when I go to Disk utility from system/administration, I get a busy icon then, that's it. It stops and I don't get the disk utility. No messages or anything.

Believe me towel was in hand ready to be thrown into the middle of the ring but, I figure there are excellent cornermen (and cornerwomen) helping out in this forum!

@tedygram311
I tried the sudo blkid and here is what was displayed:
***************************Start******************************
/dev/sda1: UUID="beb8db22-5cb5-42af-aa1a-6df1a72a6cd3" TYPE="ext4" 
/dev/sda4: LABEL="New Volume" UUID="C078DC9F78DC958E" TYPE="ntfs" 
/dev/sda5: UUID="81f29137-dfc7-4301-9592-0f5f373aa51f" TYPE="swap" 
***************************End*******************************

from "Places" I used to see two "New Volume" drives. One was the XP and the other was that large storage I was using.  I now see neither one.  Although, like I mentioned before, I saw the XP one last night but, upon rebooting, I don't see it either now.

@oldfred
Thanks for the informative links. Some I had read through, many I hadn't.  Many of those articles had mentioned using the Recovery console within the XP setup process (or fixing the boot.ini ut from within XP.)  But, I never got that option when I ran the setup those three times. Maybe I was doing something wrong or the slipstream install disc (SP3 and sata drivers) I made omitted it.

I didn't quite understand the instructions for the results.txt file, so I just uploaded it, if that's ok?



I'm gonna go with the 2 separate drives.  Just not sure how I'm gonna implement them I may just get two removable bays and just push in the one I want to use at that time... unless I can learn how to do it the "normal" way.

Again thanks everyone for contributing to my "Learning Linux Knowledge" Fund.

---

### Post by oldfred on 2011-03-23
You sda3 has a mount issue. I would try chkdsk from the XP disk. 

You sda4 is not fully repaired. see the comparison of yours & mine. Try fixboot again.

Your boot.ini says it will boot from partition 1 or 3 but your only XP is in 4. You can manually edit your boot.ini to fix it, but with Ubuntu you have to be careful of line endings. See below.

```
sda3: ________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
[COLOR=Red]mount: unknown filesystem type 
[/COLOR]
sda4: ____________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR=Red]Operating System:  [/COLOR]
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda1: __________________[COLOR=Red] This is mine:[/COLOR]

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  [COLOR=Red]Windows XP[/COLOR]
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

================================ sda4/boot.ini: =============
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition([COLOR=Red]1[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition([COLOR=Red]3[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS. New versions of gedit do have the correct way to save- notice line endings combo box near save button.

If you just edit the numbers and nothing else you will not change line endings and it will be ok.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

---

### Post by crispy_420 on 2011-03-24
If you are here in the US this kit makes quick work of the swappable hard drive kit: 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817121172](http://www.newegg.com/Product/Product.aspx?Item=N82E16817121172) 

I have the IDE version and love it. The potential is limitless and takes out all the fuss of dual boot and frequent OS switches. What is real nice is the ability to cheaply (this is all relative) add a new setup. That means a new SATA drive and a new caddy. With the dropping price of drives it is a wise decision.

---

### Post by chipmcd on 2011-03-24
You're not gonna believe it.  Woke up this morning to check emails and saw that the XP partition was available in "Places".  No time to post to the forum; had to run.  Now back, it's gone again.  Arrrggg!

@oldfred
I imagine you're talking about running chkdsk from the recovery console in the XP setup?  Well I must be doing something wrong. I attached an image of what I get when the XP cd finally stops and I have to make a selection.  Like I mentioned before, I don't get the repair option.  It just wants me to select and setup, create or delete a partition.  Also, I'm sort of concerned that the large unpartitioned space is my storage space gone bye bye. Would it make a difference that I created that partition with Gparted?  Could that be why it shows up unpartitioned in the XP setup?  I'm hoping so.  

Also, never used nano before so had to do some reading last night.  I'm ready to go if I can ever get that file to show up again.
 
p.s. Blackhawks fan?

@crispy_420
Thanks for the heads up.  Newegg is about 15 or 20 miles from me.  And I got a Frys right in between us, too.

---

### Post by oldfred on 2011-03-24
You should run the repairs on the C: drive to see if you can get the partition to know it is Windows XP.

Do not know why it does not see sda3 or it must also be having trouble mounting it. You can try testdisk. See if testdisk sees sda3, it should see sda4, but I would not use testdisk on it, since windows sees it and should finalize its repair.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

More of a Bears fan, The Bears quarterback on the bench is always better than the one on the field, since the days of Billy Wade.

---

### Post by quirks on 2011-03-24
> You're not gonna believe it. Woke up this morning to check emails and saw that the XP partition was available in "Places". No time to post to the forum; had to run. Now back, it's gone again. Arrrggg!


Try mounting the partition manually, like tedygram311 suggested earlier:

First, create a mount point:

```
sudo mkdir /mnt/sda4
```

Then mount the Windows partition:

```
sudo mount UUID=C078DC9F78DC958E /mnt/sda4
```

This command should mount your Windows partition (which has the UUID C078DC9F78DC958E) to /mnt/sda4. In my experience, this technique is more reliable than the "Places" menu. If it works, I can show you how to auto-mount the partition during boot (using /etc/fstab). It is what I use with my Windows partition and it works reliably.

> Also, I'm sort of concerned that the large unpartitioned space is my storage space gone bye bye.

As oldfred pointed out earlier, this partition has some problems identifying the file system. If you are lucky, then only the file system type in the partition table was lost and the data is still there. In this case, you should be able to mount the partition manually:

Again, create a mount point:

```
sudo mkdir /mnt/sda3
```

Then, mount the partition (assuming you formatted the partition with the FAT file system):

```
sudo mount -t vfat /dev/sda3 /mnt/sda3
```

If you formatted the partition with NTFS, then use this command instead:

```
sudo mount -t ntfs-3g /dev/sda3 /mnt/sda3
```

If neither of the commands work, then this partition is likely broken, sorry.

> Like I mentioned before, I don't get the repair option.

My guess is that the Windows installation CD does not recognize the Windows partition, because the partition is not the first one on the disk. Like oldfred wrote earlier, Windows likes to be the first partition.

---

### Post by chipmcd on 2011-03-24
@oldfred
What are you gonna do if they can't get a deal together and you're faced with a lockout year?  See we have no worries about that here in LA.  We haven't had a team since the beginning of time...  or so it seems!

@quirks
Thank you.  I was able to mount the Windows partition.  And yes, sadly I think the other has left the building.

I think what I am going to do ultimately is to install the two separate hard drives into the one computer and keep the operating systems separate.  This hard drive (with the dual boot) is going to get redone fresh Ubuntu install.

One last question for all:  Could I just re-install Ubuntu on this hard drive, connect both sata drives to the motherboard and just select the hard drive I want to boot at startup (I think it's f10 to select which drive to boot on my motherboard)?  I guess I could install Ubuntu after both are connected and generate a new grub but, I sort of want to keep them completely separate until I learn more of the ins and outs of Linux, dual booting, etc.

---

### Post by oldfred on 2011-03-25
I remember the last lockout. We still had "football" (USA type to everyone else), but with all new players. Millionaires cannot agree with Billionaires. And it used to be a sport.

As long as you have a different boot loader in each drive you can use the one time boot key to choose, but grub2 will find your other installs and let you boot them. I always recommend that you do keep boot loaders for each system in the same drive so you can boot it with the one time key just in case of problems. But then use grub2 to boot everything.

But grub2 likes to install its boot loader to sda, you have to use manual install to get a choice or disconnect the other drive. Windows works best if it is the first drive. Many have had issues installing Windows as the only drive and then making it sdb as it has issues with the change. Ubuntu uses UUIDs so it will still find itself even if the drive letter changes.

---

### Post by quirks on 2011-03-25
After you have re-installed your system, here's how you can auto-mount the Windows partition during boot. This way, you will not have to rely on the "Places" menu.

Create a mountpoint:

```
sudo mkdir /mnt/windows
```

Make a backup copy of the file /etc/fstab. Then edit it using gedit or whatever your favourite text editor is:

```
gksudo gedit /etc/fstab
```

Append the following line:

```
UUID=<UUID of Windows partition as given by blkid>  /mnt/windows    ntfs-3g  rw,nosuid,nodev,noatime,allow_other,fmask=0111  0  0
```

After a reboot, the windows partition should be mounted automatically. If you want it to appear in the "Places" menu, then open Nautilus, navigate to /mnt/windows and choose Bookmarks -> Add Bookmark.

One word of warning: do not auto-mount your Windows partition, when you use the hibernation feature of Windows. If Windows is in hibernation mode and you create/rename/delete files on the Windows partition from within Linux, you may seriously screw up the Windows file system!

If you do use hibernation in Windows, then I recommend mounting it read-only in Linux. This is completely safe, but you will not be able to modify any files on Windows from Linux. To do so, change the option

```
**rw**,nosuid,nodev,noatime,allow_other,fmask=0111
```

to

```
**ro**,nosuid,nodev,noatime,allow_other,fmask=0111
```

---

### Post by oldfred on 2011-03-25
+1 on quirks suggestion of READ ONLY on windows partition.

I always suggest a separate shared partition for any data that you may want in both systems. I have used that and it works well. I have Firefox & Thunderbird data still in my shared even though I rarely boot XP now.

---

### Post by chipmcd on 2011-03-25
@quirks
thanks for the info (now logged into my notebook of learning linux.)  I don't use hibernaton at all on any computer.  I leave, I just shut 'em down.

@oldfred
that's what the big storage partition was for, sharing the space for saving XP and Linux stuff.  But now sadly she's gone.  

Just going to have two separate 500gb hard drives sharing the same computer.  Thinking about the suggestion from crispy_420 and getting a swappable bay for them.  Pull one out, push the other in.  Completely separate but, I know that they can live in a dual boot environment.  Just don't want to play around with the XP drive and my data on it.  Don't need to lose that work stuff on it even after backing it up.  

Thanks for all the great tips and help.

---

