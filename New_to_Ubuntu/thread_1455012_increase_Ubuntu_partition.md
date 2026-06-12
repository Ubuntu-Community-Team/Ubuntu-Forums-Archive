---
title: "increase Ubuntu partition"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-15
I have windoes 7 and Ubuntu on my computer.  I want to increase the size of my Ubuntu partition.  I reduced the Windows partition and now have a bunch of unallocated space but...

I can't extend the Ubuntu volume.  Strangely, I can extend the windos partition but this is not an option for Ubuntu.

Any thoughts, and any issues or problems to be aware of when extending a partition.

thanks - chirs

---

### Post by Elfy on 2010-04-15
You need to boot from either alivecd or a partition editor so that the ubuntu partition is not mounted.

You will also need to make sure swap is not being used - right click the swap partition and swapoff.

If the partition which you wish to expand is a logical partition - expand the extended partition beforehand.


BACKUP and data you would not wish to lose if anything goes awry.

It can take a while to do - do not think it has hung and turn it off.

---

### Post by Mark Phelps on 2010-04-15
Did you reduce the Win7 partition using GParted? If so, you should boot back into Win7 a couple of times to allow it to adjust the filesystem appropriately and confirm it still works.

Also, once in there, you should use the Backup feature to create and burn a Win7 Repair CD -- in case you should need this later to repair Win7 boot problems.

---

### Post by noworldorder on 2010-04-15
>  			 		   		 		 		Did you reduce the Win7 partition using GParted? 

No I reduced it in Windows 7.  I was hoping I could do everything there but it seems this will be a more complicated procedure.

---

### Post by srs5694 on 2010-04-15
The Windows partitioning tools don't understand Linux filesystems, so you can't do this in Windows -- at least, not with the standard tools. (Partition Magic used to handle at least some Linux filesystems, but I don't know its current status offhand. There may be other third-party utilities that would work, too, but again I don't know the details.)

It might help us if you could post either a screen shot of your partitions as shown by GParted or the output of the text-mode command "sudo fdisk -l" (that's a lowercase L, not a digit 1). There are several possible complications, even in GParted, and 

Another option, besides resizing partitions, is to create new ones. You can create a partition in the empty space you've got and then mount it at some convenient point in the Linux directory tree. You can then either use it as empty space or move some files into that space. For instance, you could use the new space as a /home directory (but this will entail moving your current /home directory contents first -- this isn't hard, but it is a multi-step procedure); or you could use it as a subdirectory devoted to certain file types, such as /home/{yourusername}/Music to store music files in that space. One advantage of this approach is that the risk to your current Linux installation is minimal. Moving and resizing partitions are inherently risky -- a power outage, bug, or various other problems can cause you to lose all the data in the partition you're manipulating, and sometimes in other partitions, as well.

---

### Post by noworldorder on 2010-04-15
I attached a screen shot of my partitions

---

### Post by noworldorder on 2010-04-15
Better Screen Shot...

---

### Post by Elfy on 2010-04-15
Boot the buntu cd - right click the swap partition - sda6.

You need to then move the unallocated space to the right of the extended partition, then expand the extended partition. Move the swap to the right of the unallocated space now inside the extended. Now you will be able to expand the linux partition.

Alternatively you could make a new partition with the unallocated space - make it ntfs so itcould be shared between OS's or make it ext4 for buntu.

---

### Post by srs5694 on 2010-04-15
You will need to do some changes from a boot CD or USB flash drive, as forestpiskie suggests. The reason is that you've used all four of the available primary partitions, but your only free space is outside of the extended partition that supports more partition entries. Therefore, you must expand the extended partition, but you can't do this while any of its partitions are in use, as they necessarily are while Linux is booted from the hard disk. Thus, you need to boot an emergency disc, launch GParted in it, and disable its use of swap space (if your emergency disc uses the swap space; some do and some don't).

I wouldn't bother moving the swap space, unless you wanted to increase the swap space size.

You'll have to increase the size of the extended partition (/dev/sda3); you should be able to shift its start point to the left so that it absorbs the free space you've created. Once this is done, you have three options:


[list]
[*]Move and resize /dev/sda5, your Linux root (/) partition, so that it fills all its current space and the new free space (it'll be about 76GB).
[*]Create a new partition in the free space and mount it somewhere in your Linux directory tree. You'll have a somewhat awkward split of sizes for most purposes if you do this, but depending on how you intend to use the extra disk space, it might work well.
[*]Move and resize /dev/sda5 so that it starts earlier and is *smaller* than it currently is (perhaps 10-15GB), then create a new partition to be used as /home (about 60GB) in the free space. This is a more involved manipulation than the others, but in the long term it will give you the greatest flexibility.
[/list]


Either of the last two options will require you to make changes to your /etc/fstab file to mount the new partition in a suitable location, and the last option (and perhaps the second) will require you to juggle some files around. If you want to follow either course, post again for details about how to perform these tasks.

---

### Post by noworldorder on 2010-04-15
thanks for all the help.  

so I am a total newbie.  how do I make a boot CD.  Is the Ubuntu install cd a boot cd??

thanks - chris

---

### Post by Elfy on 2010-04-15
> **noworldorder said:**
> thanks for all the help.  

so I am a total newbie.  how do I make a boot CD.  Is the Ubuntu install cd a boot cd??

thanks - chris

Yes - there is a partition editor in the System Admin menu.

---

### Post by noworldorder on 2010-04-15
excellent help - thanks

another total newbie question.  How do I get my boot cd to boot.  when I restart with the cd in the drive it just goes right to Ubuntu and ignores the cd.  I tried pressing f8 and f12 with no results.

thansk - chris

---

### Post by Elfy on 2010-04-15
f8 or f12 would do nothing for me - I have to set boot order in the BIOS

---

### Post by srs5694 on 2010-04-15
Unfortunately, there's no standardization between different BIOSes about how to change the boot order. Sometimes you've got to fit a function key (F2, F10, or something else); other times you've got to enter the BIOS setup utility (via Del, F10, or something else) and make changes. There's usually a prompt early in the boot process, but it also usually stays up for only about two seconds, so you've got to watch the screen with eagle eyes. You could try reading your motherboard's (or computer's) manual for more clues.

---

### Post by noworldorder on 2010-04-15
Okay - I got the CD to boot...

> Yes - there is a partition editor in the System Admin menu.

Why can't I find this?  I can't see a system admin menu...

---

### Post by noworldorder on 2010-04-15
I have the Ubuntu9.10 Desktop CD.  Does this have the partition editor on it?

---

### Post by noworldorder on 2010-04-15
Well I got into the partition editor but I couldn't move the unallocated space. Other partitions could be moved but not the unalocated space.  I turned off the swap section but no change.

any thoughts?

---

### Post by dummyhead3 on 2010-04-15
The unallocated space is basically nothing. Instead of moving nothing (the unallocated space), try resizing your partition called /dev/sda3 towards the left and after, resizing your Linux partition (/dev/sda5 in your case) towards the left also.

---

### Post by cuberts on 2010-04-15
> **noworldorder said:**
> I have windoes 7 and Ubuntu on my computer.  I want to increase the size of my Ubuntu partition.  I reduced the Windows partition and now have a bunch of unallocated space but...

I can't extend the Ubuntu volume.  Strangely, I can extend the windos partition but this is not an option for Ubuntu.

Any thoughts, and any issues or problems to be aware of when extending a partition.

thanks - chirsso first You will have to burn all the data that you have onto a live CD, then boot up from that. Then there should be an option called settings, then there is a tab where you can change the Ubuntu Partition.
Hope this helps.

---

### Post by garvinrick4 on 2010-04-15
Google "using gparted in ubuntu to resize partitions" pick out a good site to read about
using gparted partitioning software until you know what you are doing. They have some
with full pictures in "howtogeek.com" most times. Do not goof with your drive until you
know why and how to do it. 
 The reason you have to use the Live CD (install CD in try only mode,not install) is because
you can only change a partition when it is not mounted. With a live CD nothing is mounted on your hard drive. gparted is very good software, learn how to use it. Study first!!!

---

### Post by jerenept on 2010-04-15
yes. the ubuntu live install cd is a boot cd and comes with gparted builtin

---

### Post by noworldorder on 2010-04-15
> The unallocated space is basically nothing. Instead of moving nothing (the unallocated space), try resizing your partition called /dev/sda3 towards the left and after, resizing your Linux partition (/dev/sda5 in your case) towards the left also.

Hmmm... I can only expand to the right, not the left.

So I am stuck because I can't move unallocated space and I can't expand a partition to the left...

---

### Post by srs5694 on 2010-04-15
> **cuberts said:**
> so first You will have to burn all the data that you have onto a live CD, then boot up from that.

This is unnecessary (and somewhere between awkward and impossible, depending on exact interpretation). That said, backing up a partition before resizing or moving it is a good idea, but such backups are made to backup media (tapes, CD-Rs, recordable DVDs, removable hard disks, etc.), not to live CDs. Live CDs are used for emergency or low-level maintenance.

---

### Post by srs5694 on 2010-04-15
> **noworldorder said:**
> Hmmm... I can only expand to the right, not the left.

So I am stuck because I can't move unallocated space and I can't expand a partition to the left...

First you need to expand the extended partition (/dev/sda3 in your case) to the left.

*Then* you can expand the Linux partition (/dev/sda5 in your case) to the left.

---

### Post by noworldorder on 2010-04-15
Success! Thanks everyone...

---

