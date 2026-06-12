---
title: "OMG, all the data on my hard drive got wiped out?!!"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by frustratednerd on 2010-06-09
i'm not sure what happened, but all of a sudden, xubuntu wiped all the data from my secondary hdd. all i was trying to do was create a shortcut on my desktop to my secondary hard drive.

is there any way to get this data back? or is it gone... forever?

---

### Post by 4Orbs on 2010-06-09
Maybe the drive just un-mounted, in which case you'd see an empty folder?

---

### Post by mbzn on 2010-06-09
You could try testdisk 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

I've had good experiences, you may have to do a little reading

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Edit: Or try the above first it might be only that

---

### Post by aysiu on 2010-06-09
> **frustratednerd said:**
> 
is there any way to get this data back? or is it gone... forever? Yes, there's a way to get it back, but you'll need a third drive (external or internal).

Install the package *testdisk* by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install testdisk
``` Then run the data (not just photo, despite the misleading name) recovery program Photorec ```
sudo photorec
```

---

### Post by bodhi.zazen on 2010-06-09
First, stop using your computer from hard drive and boot to a live CD

What command(s) did you run ?

---

### Post by frustratednerd on 2010-06-09
> **aysiu said:**
> Yes, there's a way to get it back, but you'll need a third drive (external or internal).

Install the package *testdisk* by pasting this command into [the terminal]("http://www.psychocats.net/ubuntu/terminal"): ```
sudo apt-get update && sudo apt-get install testdisk
``` Then run the data (not just photo, despite the misleading name) recovery program Photorec ```
sudo photorec
```

Okay, I've done this, and now it's asking me what partition table type it is. Which one do I pick?

@bodhi.zazen: None, I had simply dragged and dropped my secondary HDD folder from Thunar onto my desktop. I had also dragged and dropped it into the 1st panel in Thunar. Then a little while after, it brought up all these dialogs and prompts (I don't remember what they were asking) that I just simply clicked "Yes" and "Yes to All" on.

---

### Post by swamytk on 2010-06-09
Usually it is PC-DOS - first one.

---

### Post by frustratednerd on 2010-06-09
Okay, well I'm running PhotoRec now. It seems to be working nicely. Now all I have to do is wait about 4 hours.

---

### Post by aysiu on 2010-06-09
> **swamytk said:**
> Usually it is PC-DOS - first one.
If you're running Xubuntu, I don't think there is a usual.

It could be FAT32 or Ext4 or Ext3, or even NTFS.

```
sudo fdisk -l
``` will tell you.

---

### Post by mbzn on 2010-06-09
And after that you'll have to sort all the files(better than loosing them)

---

### Post by frustratednerd on 2010-06-09
@mbzn: What do you mean by "sort all the files"? As in like, sorting them alphabetically, or do you mean something else?

---

### Post by aysiu on 2010-06-09
> **frustratednerd said:**
> @mbzn: What do you mean by "sort all the files"? As in like, sorting them alphabetically, or do you mean something else?
When the files are recovered, only the files themselves are not recovered, not the original names of the files or their original locations.

It's up to you to reorganize everything.

---

### Post by frustratednerd on 2010-06-09
Oh shoot. Really?

Okay. Thanks.

---

### Post by srs5694 on 2010-06-09
> **4Orbs said:**
> Maybe the drive just un-mounted, in which case you'd see an empty folder?

IMHO, everybody else has jumped to conclusions. You should step back and consider other alternatives, such as the one 4Orbs has suggested.

For starters, post the output of the following command, typed at a text-mode shell prompt: "sudo fdisk -lu". This will show what partitions are defined on all your disks. Chances are your secondary drive is /dev/sdb. If it's got just one partition (/dev/sdb1, in all likelihood), you could try manually mounting it: "sudo mount /dev/sdb1 /mnt". If the files reappear in /mnt, then all is well, and you just need to figure out why the disk isn't mounting or was unmounted.

There are other possible causes, but more data is necessary to properly diagnose the situation, starting with the "sudo fdisk -lu" output. You could also try simply rebooting the computer; that might fix certain types of problems.

---

### Post by srs5694 on 2010-06-09
> **aysiu said:**
> [quote=swamytk]Usually it is PC-DOS - first one. 	If you're running Xubuntu, I don't think there is a usual.

It could be FAT32 or Ext4 or Ext3, or even NTFS.[/QUOTE]

Swamytk's message was in response to the question of what partition table type the disk uses. Examples are MBR (aka MS-DOS), APM, GPT, and BSD disklabel. This is entirely independent of the filesystem type, some of which you've listed.

---

### Post by frustratednerd on 2010-06-09
> **srs5694 said:**
> IMHO, everybody else has jumped to conclusions. You should step back and consider other alternatives, such as the one 4Orbs has suggested.

For starters, post the output of the following command, typed at a text-mode shell prompt: "sudo fdisk -lu". This will show what partitions are defined on all your disks. Chances are your secondary drive is /dev/sdb. If it's got just one partition (/dev/sdb1, in all likelihood), you could try manually mounting it: "sudo mount /dev/sdb1 /mnt". If the files reappear in /mnt, then all is well, and you just need to figure out why the disk isn't mounting or was unmounted.

There are other possible causes, but more data is necessary to properly diagnose the situation, starting with the "sudo fdisk -lu" output. You could also try simply rebooting the computer; that might fix certain types of problems.

Here you are. But I've already run PhotoRec, so I'm not sure how that's gonna affect things.

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eaf35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   149792767    74895360   83  Linux
/dev/sda2       149794814   156248063     3226625    5  Extended
/dev/sda5       149794816   156248063     3226624   82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000fcc90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   268430084   134215011    7  HPFS/NTFS
/dev/sdb2       268430085   514385234   122977575    7  HPFS/NTFS
/dev/sdb3       514385235   586067264    35841015    f  W95 Ext'd (LBA)
/dev/sdb5       514385298   581986754    33800728+  83  Linux
/dev/sdb6       581986818   586067264     2040223+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x439b1673

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001    7  HPFS/NTFS3rd drive is my external.

---

### Post by srs5694 on 2010-06-09
It looks like the drive in question has a partition defined, and it's most likely NTFS.

First, in any sort of data recovery scenario, it's always best to do a complete low-level backup of the disk, but this would take another 1.5TB (or bigger) drive, and it may be overkill in this case.

I'd first try mounting it manually, as I suggested earlier, just with a change to the device filename: "sudo mount /dev/sdc1 /mnt". If that works, you'll see your files in /mnt. If it doesn't work, you'll see some sort of error message. Post that.

My suspicion is that the drive was not cleanly unmounted at some point. When this happens on an NTFS drive, it must be checked *in Windows* using the Windows CHKDSK program. I believe there's a GUI option somewhere in Windows for this, or you can run CHKDSK from a Windows command prompt. I'm not an expert on Windows, though, so I can't provide details off the top of my head. You can also run the Linux ntfsfix program, as in "sudo ntfsfix /dev/sdc1", to do a few very basic checks and flag the partition for checking in Windows. Note that you may need to run several checks in Windows before the disk is completely clean. After this is done, with any luck you'll be able to access the files from both Windows and Linux.

---

### Post by frustratednerd on 2010-06-09
> **srs5694 said:**
> It looks like the drive in question has a partition defined, and it's most likely NTFS.

First, in any sort of data recovery scenario, it's always best to do a complete low-level backup of the disk, but this would take another 1.5TB (or bigger) drive, and it may be overkill in this case.

I'd first try mounting it manually, as I suggested earlier, just with a change to the device filename: "sudo mount /dev/sdc1 /mnt". If that works, you'll see your files in /mnt. If it doesn't work, you'll see some sort of error message. Post that.

My suspicion is that the drive was not cleanly unmounted at some point. When this happens on an NTFS drive, it must be checked *in Windows* using the Windows CHKDSK program. I believe there's a GUI option somewhere in Windows for this, or you can run CHKDSK from a Windows command prompt. I'm not an expert on Windows, though, so I can't provide details off the top of my head. You can also run the Linux ntfsfix program, as in "sudo ntfsfix /dev/sdc1", to do a few very basic checks and flag the partition for checking in Windows. Note that you may need to run several checks in Windows before the disk is completely clean. After this is done, with any luck you'll be able to access the files from both Windows and Linux.
Alright. Just tried it, and at first when I typed it in and pressed enter, nothing appeared, so I had to do it again, and it gave me this error message:

"Device or resource busy"

Hm, odd. I just tried to manually mount the first partition a 2nd time, but it said it was already mounted on /mnt. How do I access /mnt so I can see my files? Well, I finally discovered where /mnt was, and all the folders and such were recovered, but NOT the files.

Also tried to manually mount the second partition a 2nd time, but it gave me another "Device or resource busy" error message.

EDIT: Sorry for all the different occurrences and such. I just rebooted the computer and tried to manually mount the first partition again. Success! Files from my first partition appeared in /mnt.

However, I am still getting a "Device or resource busy" error when I try to manually mount the second partition. Perhaps running PhotoRec on the 2nd partition has caused this?

---

### Post by frustratednerd on 2010-06-09
UPDATE: Turns out that the drive was simply un-mounted.

When I remounted the 1st partition, all the files and folders showed up in /mnt. When I remounted the 2nd partition, however (the one that I ran PhotoRec on), only the folders and none of the files showed up.

---

### Post by aysiu on 2010-06-09
> **srs5694 said:**
> Swamytk's message was in response to the question of what partition table type the disk uses. Examples are MBR (aka MS-DOS), APM, GPT, and BSD disklabel. This is entirely independent of the filesystem type, some of which you've listed. I assumed the OP had simply misspoken, since I've run Photorec a number of times, and not once has it asked for a partition table type, only a filesystem type.

---

### Post by 4Orbs on 2010-06-09
> When I remounted the 1st partition, all the files and folders showed up in /mnt. When I remounted the 2nd partition, however (the one that I ran PhotoRec on), only the folders and none of the files showed up.
Were you trying to mount the second partition on /mnt while the first was already mounted there? To work correctly you'd need to unmount the first before trying to mount the second.

---

### Post by frustratednerd on 2010-06-09
> **4Orbs said:**
> Were you trying to mount the second partition on /mnt while the first was already mounted there? To work correctly you'd need to unmount the first before trying to mount the second.

Oh, okay. Is there anyway to do that without restarting the computer?

---

### Post by 4Orbs on 2010-06-09
```
sudo umount /dev/sdc1
```
Then to mount a different partition:
```
sudo mount /dev/sdc2 /mnt
```
Be sure to change the scd2 to whatever is the correct partition name.

---

### Post by frustratednerd on 2010-06-09
Okay, thanks.

Well, it turns out that running PhotoRec erased all the files off of the 2nd partition, leaving just the folders there. 

All the files and folders on the 1st partition are still there.

What should I do now? Seeing as now that all the data from my 2nd partition IS now erased (since I already extracted them using PhotoRec)?

---

### Post by aysiu on 2010-06-09
If Photorec erased your second partition, then you didn't use it correctly.

Photorec does not *move* or erase files off the partition or drive it's trying to recover files from.

It *copies* those files to a new location of your choosing (an external hard drive, a third internal hard drive).

My guess is that you somehow chose the 2nd partition as your save location for recovered files instead of the source location to recover from.

---

### Post by frustratednerd on 2010-06-09
Oops, guess I worded my response kind of awkwardly. What I meant to say, was that PhotoRec had "recovered" my "deleted" files from my 2nd partition (which weren't deleted at all, it was just that the 2nd hard drive wasn't mounted for some reason, 'causing me to believe that all the files were deleted) to my external HDD, and that now when I mount the 2nd partition, none of the files are there anymore, just the folders.

On my external HDD where I "recovered" the files, a lot of the folders it created for the "recovered files" had a bunch of TXT files with meaningless gibberish in them, along WITH the files from my partition.
Here's what I'm talking about:

[http://imgur.com/HvowJ.png](http://imgur.com/HvowJ.png)
[http://imgur.com/f91S0.png](http://imgur.com/f91S0.png)

Is there a way for PhotoRec to "put" the files back onto the 2nd partition again?

What do I do now?

---

### Post by SushiR on 2010-06-10
> **frustratednerd said:**
> Okay, I've done this, and now it's asking me what partition table type it is. Which one do I pick?

@bodhi.zazen: None, I had simply dragged and dropped my secondary HDD folder from Thunar onto my desktop. I had also dragged and dropped it into the 1st panel in Thunar. Then a little while after, it brought up all these dialogs and prompts (I don't remember what they were asking) that I just simply clicked "Yes" and "Yes to All" on.

Maybe I'm getting this wrong, but I think you just copied everything from your secondary HDD onto your Desktop (directory). If so, the files must be there...

---

### Post by frustratednerd on 2010-06-10
Someone please read my latest post. It has everything you need to know.

---

### Post by srs5694 on 2010-06-10
> **frustratednerd said:**
> UPDATE: Turns out that the drive was simply un-mounted.

When I remounted the 1st partition, all the files and folders showed up in /mnt. When I remounted the 2nd partition, however (the one that I ran PhotoRec on), only the folders and none of the files showed up.

Initially you said the problem was with /dev/sdc, which your fdisk output shows has just one partition. Thus, it's extremely unclear to me what you mean by "1st partition" and "2nd partition". Please specify these clearly using Linux device identifiers (/dev/sdc1, etc.).

If the problem partition is an NTFS drive, I still think that using Windows' CHKDSK is a good idea. Linux has very poor NTFS recovery capabilities, at best; you really *must* use Windows for NTFS data recovery, at least if you expect to recover everything in situ. (PhotoRec can identify and copy files on a variety of filesystems, but that's a low-level data copy, not a filesystem repair.)

---

### Post by bodhi.zazen on 2010-06-10
> **srs5694 said:**
> If the problem partition is an NTFS drive, I still think that using Windows' CHKDSK is a good idea. Linux has very poor NTFS recovery capabilities, at best; you really *must* use Windows for NTFS data recovery, at least if you expect to recover everything in situ. (PhotoRec can identify and copy files on a variety of filesystems, but that's a low-level data copy, not a filesystem repair.)

+1

It is for this reason, if one no longer runs Windows, I advise against using FAT or NTFS partitions.

For cross platform compatibility I personally have less problems with FAT (I do not transfer 4 + GB files).

---

### Post by frustratednerd on 2010-06-10
> **srs5694 said:**
> Initially you said the problem was with /dev/sdc, which your fdisk output shows has just one partition. Thus, it's extremely unclear to me what you mean by "1st partition" and "2nd partition". Please specify these clearly using Linux device identifiers (/dev/sdc1, etc.).

If the problem partition is an NTFS drive, I still think that using Windows' CHKDSK is a good idea. Linux has very poor NTFS recovery capabilities, at best; you really *must* use Windows for NTFS data recovery, at least if you expect to recover everything in situ. (PhotoRec can identify and copy files on a variety of filesystems, but that's a low-level data copy, not a filesystem repair.)
Sorry for being unclear. In my original post, I had stated that the problem was with my secondary HDD (sdb). Therefore, what I mean by "1st partition" and "2nd partition" is /dev/sdb1 and /dev/sdb2.

Alright, since all I have on this computer is Xubuntu, do you recommend that I install Windows and dual-boot it with Xubuntu (for chkdsk)?

---

### Post by srs5694 on 2010-06-11
> **frustratednerd said:**
> Sorry for being unclear. In my original post, I had stated that the problem was with my secondary HDD (sdb). Therefore, what I mean by "1st partition" and "2nd partition" is /dev/sdb1 and /dev/sdb2.

Alright, since all I have on this computer is Xubuntu, do you recommend that I install Windows and dual-boot it with Xubuntu (for chkdsk)?

No, if those partitions are data partitions only, I recommend you use a [Windows emergency CD/DVD](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) for filesystem recovery, then copy the files over to another partition, create a fresh Linux-native filesystem in place of NTFS, and copy the files back. Using NTFS on a Linux-only system is pointless at best and dangerous at worst, and adding a Windows dual-boot just to enable filesystem checks is a ridiculous waste of disk space and money, and rebooting to Windows to perform the periodic disk checks that would be required will also waste time. It's far better to stick to OS-native filesystems whenever possible, no matter what OS you're using. Violate this rule only when you need to interchange data with another OS, as in dual-boot configurations or when using removable media that must be read on multiple OSes.

---

### Post by frustratednerd on 2010-06-11
> **srs5694 said:**
> No, if those partitions are data partitions only, I recommend you use a [Windows emergency CD/DVD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") for filesystem recovery, then copy the files over to another partition, create a fresh Linux-native filesystem in place of NTFS, and copy the files back. Using NTFS on a Linux-only system is pointless at best and dangerous at worst, and adding a Windows dual-boot just to enable filesystem checks is a ridiculous waste of disk space and money, and rebooting to Windows to perform the periodic disk checks that would be required will also waste time. It's far better to stick to OS-native filesystems whenever possible, no matter what OS you're using. Violate this rule only when you need to interchange data with another OS, as in dual-boot configurations or when using removable media that must be read on multiple OSes.
Oh I see. So what you're recommending is that I use ext4 in place of NTFS?

---

