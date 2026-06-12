---
title: "Questions about disk cloning with dd"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-09-11
When cloning one drive to another, does the target hard drive have to be formatted, or will dd effectively mirror everything, data and partitions, formatting on the fly?

If formatting is performed on the fly, is the formatting the same, e.g., ext4 --> ext4?

If the target drive is twice the size of the source drive, is the remaining space available to Gparted later, or is formatting and partitioning in advance necessary anyway to use this space in the future?

Thanks

kirby

---

### Post by AlphaLexman on 2010-09-11
> **KirbySmith said:**
> When cloning one drive to another, does the target hard drive have to be formatted, or will dd effectively mirror everything, data and partitions, formatting on the fly?

If formatting is performed on the fly, is the formatting the same, e.g., ext4 --> ext4?

If the target drive is twice the size of the source drive, is the remaining space available to Gparted later, or is formatting and partitioning in advance necessary anyway to use this space in the future?

Thanks

kirby

NO!

You HAVE to partition and format the destination drive first. The format type does not HAVE to match, but for safety (and journaling) sake, it should.

---

### Post by Herman on 2010-09-11
> When cloning one drive to another, does the target hard drive have to be  formatted, or will dd effectively mirror everything, data and  partitions, formatting on the fly?The dd command will mirror everything.
> If formatting is performed on the fly, is the formatting the same, e.g., ext4 --> ext4?That's because dd command works at raw disc level, so the dd command mirrors the boot sectors and file system blocks as well as files, and even empty sectors in the disc. (Thats's why if you make a mistake with dd and run it backwards it can copy an empty disk to the one with data in it, thereby removing all the data).  Therefore, your file system will be a perfect mirror of the original. 

If you will be booting without removing the clone of the original disk it will have the same file system UUID number, so you will need to use an tune2fs command with the -U option to change the UUID number in one of copy, (man tune2fs). Then you'll need to edit /etc/fstab in the operating system with the changed file system UUID and run either sudo grub-mkconfig or update-grub, whichever your prefer. 
If you will be removing one disk or the other you don't need to do anything though.
> If the target drive is twice the size of the source drive, is the  remaining space available to Gparted later, or is formatting and  partitioning in advance necessary anyway to use this space in the  future?Yes, you will be able to resize your partitions with GParted to take up the available space in the larger hard disk. :D

---

### Post by bodhi.zazen on 2010-09-11
dd will do it all, although there are some caveats.

If you use dd to copy the entire HD , dd will copy the BR (partition table) + partitions.

dd if=dev/sda of=sdb

If you copy only a partition, the target partition must be the same size (in cylinders) as the source.

See :

[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)

[http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/](http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/)

After cloning a partition in this way, you may need to manually update grub and /etc/fstab afterwards.

---

### Post by aysiu on 2010-09-11
I would recommend using CloneZilla instead.

Even though it will overwrite the destination drive, the clone image itself will be only as large as the used space on the source drive. For example, if you have a 250 GB hard drive, but you're using only 50 GB of it, the CloneZilla image will be about 50 GB. If you use *dd*, it will copy the entire 250 GB.

And, like *dd*, you do not have to reformat the destination drive first. From [the CloneZilla FAQ](http://drbl.org/faq/fine-print.php?path=./2_System/99_format_the_destination_disk_before_cloning.faq#99_format_the_destination_disk_before_cloning.faq): > Clonezilla will create the file system for you, i.e. everything on the destination disk will be overwritten, no matter it's an unformatted disk, or a formatted disk with data on that. //NOTE// Before using Clonezilla, remember to back up the important data on the destination disk if you have. The destination drive, however, must be either the same size or larger than the source drive, so you can clone a 250 GB hard drive to another 250 GB hard drive or to a 500 GB hard drive, but you cannot clone a 250 GB hard drive to a 160 GB hard drive.

---

### Post by Herman on 2010-09-11
I agree with bodhi.zazen's concerns , if you just use the plain, bare-bones dd command you'll be copying the MBR too, which is okay if the two disks are identical, but for non-identical sized disks, you can skip the MBR with the skip option if you want to.
```
dd if=/dev/sda skip=1 of=/dev/sdb seek=1 bs=4k conv=noerror
```awesome machine's [Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") used to include that, but now he removed the whole-disk version of the command, and replaced it with a different version which includes the MBR, and is for cloning a hard disk to an external hard disk for a backup, so you can clone it back again if a disaster destroys files in the internal disk, so he includes the MBR now.
So, it depends what you're doing and how you use the command.

---

### Post by HermanAB on 2010-09-12
Hmm, Data Definition is a low level command that simply copies bytes - whichever bytes you tell it to.

The reason for the confusion is that you could tell dd to copy a disk, or a partition, or you can copy a disk, but offset the start till after the MBR, or whatever.  So you need to know what you are doing before you start.

---

### Post by Herman on 2010-09-12
:-k Bearing in mind that this is the Absolute Beginner's Talk section of the forums, I would have to agree with aysiu too, the dd command is fast, but it's not very safe for beginners
Programs like Clonezilla and Partimage are much safer. :)

---

### Post by KirbySmith on 2010-09-12
Thank you all.  

My plan was to use dd from a live CD to clone a 160 GB PATA boot disk to a more ruggedized 320 GB SATA disk.  Thereafter, only the clone would be used when booting from a hard drive.

dd seemed less complicated than Clonezilla, and it was unclear to me whether Clonezilla could be installed into and run from RAM when using the live CD.

Herman raises an interesting question -- if the MBR on a 320 GB drive is a copy of one from a 160 GB drive, what undesirable effects occur?  

I suppose that I could put an MBR on the larger drive with Gparted [I think], use Herman's suggested command to clone the smaller drive's content onto the larger drive, remove the source drive, and then use the live CD to re-establish grub's boot conditions correctly on the cloned drive per the Community Grub2 documentation. 

kirby

---

### Post by bodhi.zazen on 2010-09-12
gparted will copy / paste partitions if you wish.

---

### Post by aysiu on 2010-09-12
> **KirbySmith said:**
> 
dd seemed less complicated than Clonezilla, and it was unclear to me whether Clonezilla could be installed into and run from RAM when using the live CD. *dd* is simpler, for sure. If you wanted to run CloneZilla, you could install it and run it from RAM, but it's a lot easier to just download the CloneZilla live CD (much smaller than the Ubuntu .iso).

Whether you go Ubuntu with *dd*, Ubuntu with CloneZilla, or just CloneZilla, you can save yourself a blank CD, though, by "burning" the .iso to USB with [UNetbootin](http://unetbootin.sourceforge.net)

---

### Post by KirbySmith on 2010-09-12
Thanks for the information summary, aysiu.  I have to confess that I didn't need any USB thumb drives for what I did on Win2k "back in the day" before the purported factory-supplied USB trojan problem, and haven't bought any since then.  Time to embrace the 21st century, I suppose.  There is at least one company manufacturing (not inexpensive) models in the US that should be clean.

In the mean time, I can safely (i.e., not have high data loss risk) experiment with dd on a new PC under construction and test.  This PC is running from a  160 GB IDE drive cloned using EzRaid hardware from the IDE boot drive on my present older primary computer .  The EzRaid is PATA, however, so moving to SATA boot drives requires another approach to cloning, such as using dd.

kirby

---

### Post by KirbySmith on 2010-09-17
Well, the test result was unexpected.  The test:

A new blank 320 GB SATA drive was added to the Desktop 2 PC, and the PC was then booted, resulting in the new 320 GB drive appearing as sda, and the 160 GB PATA boot drive appearing as sdb.

The new drive was given a partition table using Gparted to provide an MBR, but no partitions were created, as I expected them to be written over when dd was used.

The PC was then rebooted from the LiveCD.  Herman's method of cloning beyond the MBR using dd was used in the form

```
sudo dd if=/dev/sdb skip=1 of=/dev/sda seek=1 bs=4k conv=noerror
```where sda and sdb are reversed from his listing because of the particular naming of the two drives.

Two hours of apparent reading and writing concluded with a seemingly happy dd run reporting the same values written as read, but the new drive did not appear in Nautilus.

When I looked at the drives using Gparted or Palimpsest, the 320 GB drive appeared to be empty except for an MBR.  There were no partitions or files shown.  The 160 GB boot drive appeared to be unchanged, so it wasn't written over.   

"Sudo blkid" only shows the 160 GB drive's partitions.  I must have left out an important step in this process, and 160 GB of bits must have gone to the great bit bucket in the sky, or else they are on the new drive, but not accessible to the OS.  Maybe some arcane command string is needed to make them available.

This isn't a big deal as I can experiment with other approaches to cloning, but I would sure like to know what the error was in the test process.

Thanks for any help

kirby

---

### Post by tgalati4 on 2010-09-17
This has worked for me:

sudo cp /dev/sda /dev/sdb

Make sure /dev/sda is your data drive and /dev/sdb is your blank drive.  The reverse can be bad.  Verify with:

sudo fdisk -l

After copying, then use gparted to either grow the existing partition to fill up the space, or simply add a new data partition.

---

### Post by KirbySmith on 2010-09-19
My second test followed bodhi.zazen's GParted copy suggestion.  It worked (with some effort) and I believe it to be a better approach when the drives are unequal and one also wants to grow the swap space.

Using the new larger drive with MBR established by GParted, I copied the first partition of the old drive to the new drive using GParted's copy and paste function for partitions.  This copy functionality is not available for the extended partition that the swap space was on.  However, creating the extended partition with GParted in the remaining drive space was straightforward, and establishing a swap partition within it was easy given that swap is one of the options for the types of partitions.

I made the drive bootable using the check box in Palimpsest.

While still using the live CD, I then used Method 3 of Reinstalling Grub 2 from the Community documentation for Grub2 to ensure that the boot process would point at the correct partition.  

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Booting at this point hanged into a kind of semi-operability because the boot process couldn't find the UUID that fstab was expecting for the swap space.  (An all white screen is a bit disconcerting.)   fstab listed the old swap UUID, not the new UUID, because fstab was a copy of fstab from the old drive.  

Guessing where the Applications label was at the top of the white screen, I clicked there and got a menu and hence a terminal.  Alternatively, the live CD could be used to get to the boot drive's fstab.  The wrong UUID was fixed by pasting in the correct UUID for the swap space partition over the incorrect UUID.

(The UUID is available by running "sudo blkid" in a terminal.)

Editing fstab can be performed using

```
gksu gedit /etc/fstab
```if booting from the same drive.  If booting from the live CD, the mount path will need to be included to get to the correct /etc directory.

After this the new larger drive booted normally and all functions tested so far have worked as before on the older drive.

Again, thanks everyone for your help.  I'm marking the thread solved even though dd did not work as expected for some reason.

kirby

---

### Post by bodhi.zazen on 2010-09-20
Glad you got it sorted. I thought I mentioned updating grub and fstab in my origional post =)

using dd is similar, but you have to fix / debug any problems on your own. Installing grub of course fixes the MBR problem you had.

Not sure about the rest, can't tell from what you posted.

---

### Post by mikechant on 2010-09-20
> This isn't a big deal as I can experiment with other approaches to cloning, but I would sure like to know what the error was in the test process.

I think the missing step was to edit the partition table to point to the cloned partition; or in this case you could have copied the MBR (containing the partition table) instead of skipping it in the dd command.

---

### Post by Herman on 2010-09-20
I think so too, TestDisk is the program I use for updating a partition table.

Thank you for detailing your experience, kirby smith, so GParted can copy a partition from one disk to another now! Cool! :)

---

### Post by bodhi.zazen on 2010-09-20
> **Herman said:**
> I think so too, TestDisk is the program I use for updating a partition table.

Thank you for detailing your experience, kirby smith, so GParted can copy a partition from one disk to another now! Cool! :)

FYI: GParted has been able to do this (copy partitions) for some time. gparted is used primarily for resizing partitions or changing labels so not everyone is aware of all the features.

---

### Post by KirbySmith on 2010-09-20
> **mikechant said:**
> I think the missing step was to edit the partition table to point to the cloned partition; or in this case you could have copied the MBR (containing the partition table) instead of skipping it in the dd command.
 
Ah! I was "afraid" to copy the MBR because I assumed that it somehow incorporated the full size of the hard drive, and if derived from a 160 GB drive would thereby exclude visibility into the second 160 GB of the 320 GB drive. This assumption may be false. Or if true, GParted may be able to see through it and still partition into the second 160 GB.
 
Herman: Until now I hadn't heard of TestDisk. I'll have to look into it. 
 
bodhi.zazen: You did indeed mention grub and fstab; I wanted to provide a cookbook type of description to benefit inductive people like me and those who may not have the time to experiment. 
 
In my view, the richness of the Linux command language (including embedded programs) -- the number of commands, the scope of commands, and the multiplicity of their switches -- greatly exceeds that of either the DOS shell commands or those of earlier machines, such as the PDP-10. It can be daunting to step into this knowledge pool and discover that there is little wading area, the bottom is quicksand, and poor swimming technique attracts data-devouring sharks.
 
Again, thanks all
 
kirby

---

### Post by Herman on 2010-09-21
> FYI: GParted has been able to do this (copy partitions) for some time.  gparted is used primarily for resizing partitions or changing labels so  not everyone is aware of all the features.
:) Yes, I have been using GParted since about GParted Live Alpha3 0.0.9, since long before GParted was included in Ubuntu, and I have known for a long time that it can copy and paste partitions, (in the same disk). I just wasn't aware it was able to copy a partition from one disk and paste it in another. I think that must be a relatively recent advancement, or I'm not spending enough quality time with my computers. :)

---

### Post by bodhi.zazen on 2010-09-21
> **Herman said:**
> :) Yes, I have been using GParted since about GParted Live Alpha3 0.0.9, since long before GParted was included in Ubuntu, and I have known for a long time that it can copy and paste partitions, (in the same disk). I just wasn't aware it was able to copy a partition from one disk and paste it in another. I think that must be a relatively recent advancement, or I'm not spending enough quality time with my computers. :)

Oh, OK, not sure myself, I stopped copying partitions, backing up the entire system long ago. I just keep data and a few custom config files. Much easier to back up and restore they trying to restore every file in /usr =)

---

