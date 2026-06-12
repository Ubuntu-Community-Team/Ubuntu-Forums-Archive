---
title: "Whole Drive Unallocated."
date: 2010-11-06
forum: New to Ubuntu
---

### Post by MadDogTen on 2010-11-06
So, while trying to fix another problem, I caused this:

My WHOLE Drive is showing up as "Unallocated" on Gparted. Using Ubuntu 10.04 Live CD.


However on the Disk Utility it shows all of them, and I can still access my Old Partition and look at the files.




Here is the Result of running "sudo fdisk -l":

"
 ubuntu@ubuntu:~$ sudo fdisk -l
Ignoring extra extended partition 4
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              14       23403   187880175    5  Extended
/dev/sda3           25859       38913   104856576    7  HPFS/NTFS
/dev/sda4           23404       25859    19726337    5  Extended

Partition table entries are not in disk order
"



I absolutely NEED the files on my "E Drive" (or Backup Drive [or SDA3])

---

### Post by Hippytaff on 2010-11-06
In the first instance, if you can still see the files back them up :-)

---

### Post by MadDogTen on 2010-11-06
> **Hippytaff said:**
> In the first instance, if you can still see the files back them up :-)
I thoght about that, but I have no where to back them up to as it was the backup partition :eek:



I will be screwed if the drive ever broke, however I was thinking of Putting all the Important Files in DropBox after this (I cannot right now because its FOLDERS full of files, and I would have to do it 1 at a time, using their program I can just drag them into a folder, but as I said I am using the Live CD [and I'm not even sure they have a program for Ubuntu]).

---

### Post by Hippytaff on 2010-11-06
Can you burn them to dvd/cd or put them on a usb drive?

---

### Post by coffeecat on 2010-11-06
This is a known issue with Gparted. Have a look at this paper written by forum member srs5694:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

To see whether your 'unallocated' is due to the extra extended partition that fdisk is worried about, or due to what is described in that link, please repeat fdisk, but this time post the output of:

```
sudo fdisk -lu
```

---

### Post by MadDogTen on 2010-11-06
> **coffeecat said:**
> 
To see whether your 'unallocated' is due to the extra extended partition that fdisk is worried about, or due to what is described in that link, please repeat fdisk, but this time post the output of:

```
sudo fdisk -lu
```
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo fdisk -lu

ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ Ignoring extra extended partition 4
Ignoring: command not found
ubuntu@ubuntu:~$ Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ Disk /dev/sda: 320.1 GB, 320072933376 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
ubuntu@ubuntu:~$ 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
255: command not found
ubuntu@ubuntu:~$ Units = sectors of 1 * 512 = 512 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
ubuntu@ubuntu:~$ Sector size (logical/physical): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ I/O size (minimum/optimal): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ Disk identifier: 0x000e0e77
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
ubuntu@ubuntu:~$ /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
bash: /dev/sda1: Permission denied
ubuntu@ubuntu:~$ Partition 1 does not end on cylinder boundary.
Partition: command not found
ubuntu@ubuntu:~$ /dev/sda2          208845   375969194   187880175    5  Extended
bash: /dev/sda2: Permission denied
ubuntu@ubuntu:~$ /dev/sda3       415422464   625135615   104856576    7  HPFS/NTFS
bash: /dev/sda3: Permission denied
ubuntu@ubuntu:~$ /dev/sda4       375969790   415422463    19726337    5  Extended
bash: /dev/sda4: Permission denied
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ Partition table entries are not in disk order
Partition: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$












As I was pretty sure that wasn't right, I closed it and Tried again, and got:

ubuntu@ubuntu:~$ sudo fdisk -lu
Ignoring extra extended partition 4
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          208845   375969194   187880175    5  Extended
/dev/sda3       415422464   625135615   104856576    7  HPFS/NTFS
/dev/sda4       375969790   415422463    19726337    5  Extended

Partition table entries are not in disk order
ubuntu@ubuntu:~$


But that one is the same as the first one I posted.

---

### Post by coffeecat on 2010-11-06
OK. The partitions do not seem to be overlapping and the last sector of your partitions is not beyond the physical end of the drive (which is the problem described in the link and which I had to recover from). I would guess, therefore, that this might be the problem:

> **MadDogTen said:**
> Ignoring extra extended partition 4
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

But I'm out of my depth here and do not know what to suggest next. Certainly, back up your data. It is probably not in immediate danger so long as you don't use any partitioning software. But if someone can tell you how to edit the partition table to correct this, you certainly do want to backup first.

Perhaps srs5694 will happen along. He would certainly be able to advise.

**Edit:** what might be useful would be to backup your partition table with:

```
sfdisk -d /dev/sda > Desktop/parts.txt
```Post the contents of parts.txt so that someone can have a look at it. Make sure you get the '>' the right way round.

> **MadDogTen said:**
> But that one is the same as the first one I posted.

No, it isn't. fdisk -lu shows sectors, not cylinders, which is what we needed.

---

### Post by MadDogTen on 2010-11-06
> **coffeecat said:**
> OK. The partitions do not seem to be overlapping and the last sector of your partitions is not beyond the physical end of the drive (which is the problem described in the link and which I had to recover from). I would guess, therefore, that this might be the problem:



But I'm out of my depth here and do not know what to suggest next. Certainly, back up your data. It is probably not in immediate danger so long as you don't use any partitioning software. But if someone can tell you how to edit the partition table to correct this, you certainly do want to backup first.

Perhaps srs5694 will happen along. He would certainly be able to advise.

**Edit:** what might be useful would be to backup your partition table with:

```
sfdisk -d /dev/sda > Desktop/parts.txt
```Post the contents of parts.txt so that someone can have a look at it. Make sure you get the '>' the right way round.



No, it isn't. fdisk -lu shows sectors, not cylinders, which is what we needed.

ubuntu@ubuntu:~$ sfdisk -d /dev/sda > Desktop/parts.txt
/dev/sda: Permission denied

sfdisk: cannot open /dev/sda for reading

---

### Post by Hippytaff on 2010-11-06
Did you put sudo infront of the command?

---

### Post by MadDogTen on 2010-11-06
> **Hippytaff said:**
> Did you put sudo infront of the command?
Oh, nope.

Here now:


ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > Desktop/parts.txt

sfdisk: ERROR: sector 208845 does not have an msdos signature
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2010-11-06
> **MadDogTen said:**
> ubuntu@ubuntu:~$ sfdisk -d /dev/sda > Desktop/parts.txt
/dev/sda: Permission denied

sfdisk: cannot open /dev/sda for reading

OK. Try:

```
sudo sfdisk -d /dev/sda > Desktop/parts.txt


sudo chown yourusername: Desktop/parts.txt
```Substitute your account name for 'yourusername'.

---

### Post by coffeecat on 2010-11-06
> **MadDogTen said:**
> Oh, nope.

Here now:


ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > Desktop/parts.txt

sfdisk: ERROR: sector 208845 does not have an msdos signature
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ubuntu@ubuntu:~$

Did a parts.txt file appear on your desktop? If so, please post it.

---

### Post by MadDogTen on 2010-11-06
> **coffeecat said:**
> Did a parts.txt file appear on your desktop? If so, please post it.
Oh, yep.

Here:

"
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   204800, Id= 7, bootable
/dev/sda2 : start=   208845, size=375760350, Id= 5
/dev/sda3 : start=415422464, size=209713152, Id= 7
/dev/sda4 : start=375969790, size= 39452674, Id= 5
/dev/sda5 : start=375969792, size= 37715968, Id=83
/dev/sda6 : start=413687808, size=  1734656, Id=82
```
"



I was sitting on the First page for 20 Mins waiting for a Post without realizing there was a 2nd page. lol

---

### Post by coffeecat on 2010-11-06
Well I guess the whole problem boils down to the partition table saying that you have two extended partitions, sda2 and sda4, which is impossible. What was the 'other problem' that you were fixing that caused this?

Anyway, it's too late here for me to be able to post anything reliable and I must log off. I have tried to get some more expert help to join this thread, so perhaps they will. In the meantime, please edit your post by highlighting the parts.txt text and then clicking on the # icon which you'll find above the message field. This will enclose it in code tags and (hopefully) restore the columned formatting. Please always do this when posting code or terminal output. It is almost impossible to read otherwise. 

I'll pick this thread up in the (UK) morning.

---

### Post by MadDogTen on 2010-11-06
> **coffeecat said:**
> Well I guess the whole problem boils down to the partition table saying that you have two extended partitions, sda2 and sda4, which is impossible. What was the 'other problem' that you were fixing that caused this?

Anyway, it's too late here for me to be able to post anything reliable and I must log off. I have tried to get some more expert help to join this thread, so perhaps they will. In the meantime, please edit your post by highlighting the parts.txt text and then clicking on the # icon which you'll find above the message field. This will enclose it in code tags and (hopefully) restore the columned formatting. Please always do this when posting code or terminal output. It is almost impossible to read otherwise. 

I'll pick this thread up in the (UK) morning.
Did the Code Tag's.





Here is the link to the other problem: [http://georgia.ubuntuforums.org/showthread.php?t=1609712]("http://georgia.ubuntuforums.org/showthread.php?t=1609712")

Also, the part that isn't there (I just left the thread after that.):

I decided I was just going to Reinstall Windows, and was going to make it empty space, however I clicked the wrong button and made the space something else, after that this Current Problem Occured.

When trying to install windows it doesn't even show a Hard Drive, but I'm hoping this solves it, if not then ill make another thread.

---

### Post by srs5694 on 2010-11-06
I suspect that coffeecat is correct that the problem is two extended partitions on the disk. The sfdisk error message about sector 208845 suggests to me that /dev/sda2 should *not* be an extended partition. Try this and see what you get:

```

sudo blkid /dev/sda2

```If it returns information on a filesystem type, and perhaps a UUID value, then you should try this:


[LIST=1]
[*]Take note of /dev/sda2's sector start and end values (208845 and 375969194, respectively, according to your fdisk -lu output).
[*]Type "sudo fdisk -u /dev/sda" to edit the disk's partition table.
[*]Type "d" and enter the partition number 2.
[*]Type "n" to create a new partition. Enter the start and end values noted earlier and specify a partition type code that's suitable for the filesystem type the partition contains.
[*]Type "w" to save the changes.
[*]Type "sudo fdisk -lu /dev/sda" and see if your extended partitions (/dev/sda5 and above) reappear.
[*]Try using GParted again. With any luck it will now work.
[/LIST]

---

### Post by MadDogTen on 2010-11-06
> **srs5694 said:**
> I suspect that coffeecat is correct that the problem is two extended partitions on the disk. The sfdisk error message about sector 208845 suggests to me that /dev/sda2 should *not* be an extended partition. Try this and see what you get:

```

sudo blkid /dev/sda2

```If it returns information on a filesystem type, and perhaps a UUID value, then you should try this:


[LIST=1]
[*]Take note of /dev/sda2's sector start and end values (208845 and 375969194, respectively, according to your fdisk -lu output).
[*]Type "sudo fdisk -u /dev/sda" to edit the disk's partition table.
[*]Type "d" and enter the partition number 2.
[*]Type "n" to create a new partition. Enter the start and end values noted earlier and specify a partition type code that's suitable for the filesystem type the partition contains.
[*]Type "w" to save the changes.
[*]Type "sudo fdisk -lu /dev/sda" and see if your extended partitions (/dev/sda5 and above) reappear.
[*]Try using GParted again. With any luck it will now work.
[/LIST]
For some reason the command seems to do nothing.

I type it in, press enter, then a new thing comes up to enter something else.

Here is what it looks like: 
[http://i269.photobucket.com/albums/jj63/cooldogtwo/Ubuntu/Screenshot-8.png](http://i269.photobucket.com/albums/jj63/cooldogtwo/Ubuntu/Screenshot-8.png)

---

### Post by MadDogTen on 2010-11-06
Iv taken some screen-shots of Disk Utility and Gparted.

Here is the link:
[http://s269.photobucket.com/albums/jj63/cooldogtwo/Ubuntu/](http://s269.photobucket.com/albums/jj63/cooldogtwo/Ubuntu/)


The Large Free space and Unknown Space is what used to be Windows 7 before I messed it up.

As you see I have ubuntu installed on a 20 gig Partition, but I somehow broke it where it now cannot boot.

The E Partition is my Backup Partition.

---

### Post by coffeecat on 2010-11-07
OK. I've had a decent night's sleep, a large mug of delicious coffee and I'm ready to face a new day. :) I've had a look at your other thread and I think I've got a handle on what's happened. The part of the disc that fdisk is seeing as the "extended" partition sda2 and which Disk Utility is seeing as 192GB of "free" space, I guess is your ex-Windows C: partition. From what I understand from your other thread you've lost the filesystem anyway, but what you need to do is to edit the partition table so that it shows this as a primary, not an extended partition. After which, hopefully, Gparted will be able to make sense of it.

What I suggest you do is to follow srs5694's instructions to edit the partition table.

> **srs5694 said:**
> Take note of /dev/sda2's sector start and end  values (208845 and 375969194, respectively, according to your fdisk -lu  output).
[LIST=1]
[*]Type "sudo fdisk -u /dev/sda" to edit the disk's partition table.
[*]Type "d" and enter the partition number 2.
[*]Type  "n" to create a new partition. Enter the start and end values noted  earlier and specify a partition type code that's suitable for the  filesystem type the partition contains.
[*]Type "w" to save the changes.
[*]Type "sudo fdisk -lu /dev/sda" and see if your extended partitions (/dev/sda5 and above) reappear.
[*]Try using GParted again. With any luck it will now work.
[/LIST]


However, I've done a dummy run and I think instruction 3 needs amending, but wait till srs5694 posts back to check that I'm right. This is what I think you should need to do after 1 and 2:

Type  "n" to create a new partition. Now "p" to specify primary. Now "2" as partition number. You will now be prompted for the sectors start and end values so type in the values noted  earlier. 

Now type "t" to specify a partition system id. "2" for partition 2, and "7" for NTFS. Now you can write "w" to save the changes.

This, hopefully, will give you a partition table that shows a primary NTFS partition at sda2. If the filesystem is indeed destroyed, Gparted will show a big exclamation mark by sda2 but at least it will show sda2 and all the other partitions - hopefully. 

Don't do anything until srs5694 posts back. I hesitate to amend his instructions - he knows much more about this than I do!

Another forum use tip:

> **MadDogTen said:**
> Iv taken some screen-shots of Disk Utility and Gparted.

Here is the link:
[http://s269.photobucket.com/albums/jj63/cooldogtwo/Ubuntu/](http://s269.photobucket.com/albums/jj63/cooldogtwo/Ubuntu/)


Use the "manage attachments" button below the message field for uploading images rather than using a hosting site. It's easier for you and easier for people reading your post.

---

### Post by srs5694 on 2010-11-07
> **coffeecat said:**
> However, I've done a dummy run and I think instruction 3 needs amending, but wait till srs5694 posts back to check that I'm right. This is what I think you should need to do after 1 and 2:

Type  "n" to create a new partition. Now "p" to specify primary. Now "2" as partition number. You will now be prompted for the sectors start and end values so type in the values noted  earlier. 

Now type "t" to specify a partition system id. "2" for partition 2, and "7" for NTFS. Now you can write "w" to save the changes.

Your amendment/expansion looks correct to me; I was being a bit terse in my instructions. I also forgot that "p" doesn't prompt for the type code, but just sets it to 0x83 by default. (This always annoyed me, so it was one area where I deviated from the fdisk model when I wrote GPT fdisk!)

BTW, when blkid returns without displaying any output, it means that the program couldn't find a filesystem it recognized on the partition. It does this with a real extended partition (I just checked), but it could also do the same with a badly damaged filesystem. Thus, the blkid test I suggested came back ambiguous. If I had to bet, I'd say that your /dev/sda2 is a damaged and mis-labelled filesystem, not an extended partition, but I can't be 100% positive of that. Unfortunately, you're the one who's gambling, no matter what you do. If you win my bet, all's well. If not, you'll make it harder to recover your logical partitions. If that happens, you should still be able to recover by editing that sfdisk output you posted earlier and feeding it back into sfdisk; but we can deal with that later if it becomes necessary. I don't want to overwhelm you with contingency instructions just yet.

---

### Post by coffeecat on 2010-11-07
> **srs5694 said:**
> Unfortunately, you're the one who's gambling, no matter what you do. If you win my bet, all's well. If not, you'll make it harder to recover your logical partitions.

Nicely phrased! :)

@MadDogTen, it's important you backup your files before adjusting partitions, but I understand the quandary you're in without an external hard-drive and having to work from the live CD. There is one possible solution if you can access the ISO for Ubuntu and you have a spare USB stick of no less than 1GB. Use System > Administration > Startup Disk Creator in the live CD session to make a bootable live USB, then when you boot up with this your optical drive is spare for using blank CD/DVDs for backups.

Just a thought.

---

### Post by MadDogTen on 2010-11-07
> **coffeecat said:**
> Nicely phrased! :)

@MadDogTen, it's important you backup your files before adjusting partitions, but I understand the quandary you're in without an external hard-drive and having to work from the live CD. There is one possible solution if you can access the ISO for Ubuntu and you have a spare USB stick of no less than 1GB. Use System > Administration > Startup Disk Creator in the live CD session to make a bootable live USB, then when you boot up with this your optical drive is spare for using blank CD/DVDs for backups.

Just a thought.
Ill take the risk and hope it works, if it doesn't, well, Ill live.



Also, For the Instructions, Can you add what you said to his list then post it?

Its kinda Confusing now.

---

### Post by MadDogTen on 2010-11-07
I figured out the Instructions and Did it.

It looks to have worked exactly like you guys said as there is an exclamation point next to it.

I added the Screen-shots as attachments.

---

### Post by coffeecat on 2010-11-07
> **MadDogTen said:**
> How do I delete all the Ubuntu Partitions, and put it into 1 Partition for windows (Iv always had trouble with that [For some reason before when I deleted them, it deleted ALL the files on the Hard Drive]). I'm just going to install Ubuntu in Windows from now on.

If you mean to install Ubuntu in wubi, be aware that Ubuntu will run slower in wubi and that some people have had some nasty problems after an update with wubi installations. Be that as it may, to achieve what you want:

1 - **Backup important personal files from sda3 first.**

2 - In Gparted, right-click on the swap partition (sda6) and choose swapoff. You can't do anything with the extended/logical partitions while the live CD is using the swap partition. 

3 - Highlight each of sda6, sda5 and sda4 in turn and delete them. Do the same with sda2 for good measure.

4 - Click on Apply.

5 - Once that has finished you should have a single segment of unallocated space about 220GB showing between sda1 and sda3 (your E drive). sda3 might change to sda2 - I don't know - but so long as it is still showing as your 100GB E drive that doesn't matter.

6 - Highlight the ~220GB unallocated space > Partition > New > Primary/NTFS, and then click on Apply.

You will then have a clean NTFS partition immediately after your system reserved partition which you can tell the Windows 7 installer to use.

I hope I've got that all correct. You may want to wait until srs5694 agrees or otherwise.

---

### Post by MadDogTen on 2010-11-07
> **coffeecat said:**
> If you mean to install Ubuntu in wubi, be aware that Ubuntu will run slower in wubi and that some people have had some nasty problems after an update with wubi installations. Be that as it may, to achieve what you want:

1 - **Backup important personal files from sda3 first.**

2 - In Gparted, right-click on the swap partition (sda6) and choose swapoff. You can't do anything with the extended/logical partitions while the live CD is using the swap partition. 

3 - Highlight each of sda6, sda5 and sda4 in turn and delete them. Do the same with sda2 for good measure.

4 - Click on Apply.

5 - Once that has finished you should have a single segment of unallocated space about 220GB showing between sda1 and sda3 (your E drive). sda3 might change to sda2 - I don't know - but so long as it is still showing as your 100GB E drive that doesn't matter.

6 - Highlight the ~220GB unallocated space > Partition > New > Primary/NTFS, and then click on Apply.

You will then have a clean NTFS partition immediately after your system reserved partition which you can tell the Windows 7 installer to use.

I hope I've got that all correct. You may want to wait until srs5694 agrees or otherwise.
I was done waiting. :P

I did all of that, worked Perfectly, and Currently have Windows 7 Installed. :D



Thanks for all the help Everyone! :):)

---

