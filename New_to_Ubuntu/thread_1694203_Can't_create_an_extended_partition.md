---
title: "Can't create an extended partition"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Barnabooth on 2011-02-24
GParted doesn't allow me to create an extended partition. I have this partition schema (see screenshot 1), and I want to create an extended partition of the unallocated space, but I only get the option "primary" (screenshot 2). Maverick on a mbp5,5.

---

### Post by flee0308 on 2011-02-24
Isn't the option for a logical partition just below the primary one?

---

### Post by racie on 2011-02-24
Hmm.  Have you tried creating a LiveCD/LiveUSB of just GParted?  Once I had a similar issue formatting (though it was with a different OS), but booting into GParted fixed it.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by wilee-nilee on 2011-02-24
Right click the swap and unmount it.

---

### Post by Barnabooth on 2011-02-24
Ouch, you are fast here!
@flee the option is "shaded", that is the problem.
@racie Yes I have a (old) gparted cd. I have tried to boot into it, but it won't, might be efi-related or just an old cd. Will try again and make a new this evening.
@wilee-nilee. Sounds promising, but I probably don't understand. When I right click the swap partition i get the options (in swedish) activate / inactivate. If inactivate i can delete it. I tried that, but that didn't help creating a new extended partition (made a new swap again of course). I did not get the option mount or unmount. Am I missing something?

Have to go to work now. But thank you all for your quick answers! Will try them out more thouroughly when I get back.

---

### Post by Clever_Username on 2011-02-24
Seems like since it's unallocated space, he would have to unmount the entire drive and run gparted from a live cd like Racie suggested. I don't recall ever being able to mount or unmount something that doesn't have a drive name. sda1,sda2 etc... (sorry, don't know the right term here):D

---

### Post by Quackers on 2011-02-24
Is this the gparted from inside a mounted system? You need to use gparted from the live cd or gparted's live cd, so that the drive isn't mounted. You should also turn the swap partition off even on a live cd desktop.

---

### Post by srs5694 on 2011-02-24
I notice that your first partition is a FAT32 partition with an "EFI" label on it. This makes me think the computer may be EFI-based, in which case the disk probably uses a GUID Partition Table (GPT) rather than the older Master Boot Record (MBR) system. If I'm right in this chain of reasoning, or at least in the conclusion, you can't create an extended partition because GPT doesn't support extended partitions. Instead, you can create up to 128 partitions, which GParted identifies as primary partitions because it was written around MBR assumptions and terminology.

You can determine what type of disk you've got in several ways. The easiest may be to select View->Device Information in GParted. This will open a pane on the left side of the window with some disk information including an item called either "Partition table" or "DiskLabelType," depending on the version of GParted. If this item reads "gpt", then the disk is a GPT disk; if it reads "msdos", then it's an MBR disk. Another method is to type "sudo parted /dev/sda print". Among other things, this will produce a "Partition table" line with this information. A third way is to install [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) and type "sudo gdisk -l /dev/sda". This produces a "Partition table scan" with information on whether MBR, GPT, BSD disklabel, and Apple Partition Map (APM) data are present. This information is more complete than what GParted or parted produces, but it can be more confusing if you're unfamiliar with the possible combinations.

Finally, what type of computer is this, and what do you intend to do with the new partitions you plan to create? Some possibilities might require you to jump through some extra hoops. For instance, if you've got a BIOS-based (rather than an EFI-based) PC and you want to install Windows, you'll have to convert from GPT to MBR or create a hybrid MBR, since Windows can't boot from a GPT disk on a BIOS-based computer. OTOH, if you just want to create more partitions for use in Linux, and if the computer boots fine already, you can just create the partitions and everything should be fine, whether the computer uses an EFI or a BIOS.

---

### Post by Barnabooth on 2011-02-24
Thanks all of you for your input! I have realized that I have to run gparted live cd. And yes, the screenshots are from a mounted system, but I am able to create one or two primary partion on the unallocated space from gparted running on the harddisks ubuntu so i really don't see why i shouldn't be able to create an extended partition.

Now a second problem have arised. I have burned two different copies of gparted live cd and i am unable to boot any of them. In fact, I am unable to boot from any cd (including different live ubuntus). I have been trying with hold down numerous combinations of keys, only macs install dvd boots. The other cds spins up but stops at a certain point. Not unlike an older - - but fixed -- bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393)) 

I have been looking around to see if rEFIt should solve this particular problem, and it might or might not. But i don't have the quts to continue more today as I need to at least have a running machine tomorrow.

If anyone has any suggestions for my weekend-entertainment i would be grateful. Until then, thank you all again for your answers!

---

### Post by Barnabooth on 2011-02-24
Oh. I see you were posting when I was writing, srs5694. 

You are most certainly right that my partition table doesn't support extended partitions. I had no idea of that possibility. I will go through your post later this evening or tomorrow -- just so you don't think I am rude when not answering within short.

But for now. I plan to -- you are allowed to shrug your head -- install archlinux and a separate data-partition (not /home) for ubuntu and archlinux to access. And as I have read you shouldn't use more than 4 primary partitions I thought I had to make an extended partition as i believe EFI and swap counts as primary partitions, but -- from the quick scan of your answer, than might not necessarily be the case? Or?

Best regards.

---

### Post by Barnabooth on 2011-02-24
Sorry, macbook pro 5,5

---

### Post by Barnabooth on 2011-02-24
Read your post again srs5964, and you are right: 
sudo parted -l 
gave:

Modell: ATA ST9250315ASG (scsi)
Disk /dev/sda: 250GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: gpt

...

And from your answer and my needs I guess I can safely conclude just to make 5 primary partitions. Glad to have learned something new.
Thank you all very much!

---

### Post by srs5694 on 2011-02-24
Yes, make as many "primary" partitions as you like. (They aren't really primary partitions, since that's an MBR concept/distinction that doesn't apply to GPT disks. GParted and parted insist on applying this MBR term everywhere, though.)

It's possible that you're having problems booting most Linux CDs because Intel-based Macs are EFI-based and the CDs are designed for BIOS-based computers. Macs have a BIOS emulation mode built into their EFIs, but my understanding is that it's triggered by the presence of an MBR disk (or a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html)), so it could be that it's not working on your pure-GPT disk. If so, you might try attaching an MBR-partitioned USB flash drive or removable disk to the computer; that might enable the system to detect and boot from the CD. It's also possible that rEFIt will help on that score. I can't promise that either solution will work, though. Using a hybrid MBR might also work, but hybrid MBRs are ugly and dangerous, so I don't recommend using this approach.

---

