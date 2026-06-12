---
title: "Partition table entries are not in disk order=?Problem"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-29
Hello everyone,

Just did a  sudo fdisk -l of my newly installed OS. I had manually configured the partitions with the Live CD install to allow for my /home to be on it's own partition. The included screenshot of same indicates that my Partition table entries are not in disk order. Is this something I should correct? Can I expect problems with the partitioning as it is? If so, what should I do?

I must go to bed, and will not be available for answering of questions immediately. Sorry.

Thank you.

---

### Post by drs305 on 2009-08-29
It is not a problem. You can "reset" them to the correct order but you would need to check your grub menu and fstab in case there were any references to "sdXX" instead of to UUIDs. The reason is at least two of the partition "sdXX" designations would change after you 'reset' them.

For those wishing to do so, here is the procedure. Note that your system will operate fine without making this change and you run the risk of screwing up your boot process or partition mounting if the partition designations no longer match in fstab or menu.lst:
```

sudo fdisk /dev/sda
```
*at the prompt:*
m [I](for help)
at the prompt:[/I]
x *(extra functionality - experts only)*
f  *(fix)*
w *(write to disk and exit)*
You may get a warning that devices are in use and the new table will be used at the next boot.  
[COLOR="DarkRed"]**Check fstab and menu.lst before rebooting.**[/COLOR]
Repeat for other drives.

---

### Post by mikodo on 2009-08-29
Here's a screeshot of Gparted showing the partitions set up.

---

### Post by mikodo on 2009-08-29
> **drs305 said:**
> It is not a problem. You can "reset" them to the correct order but you would need to check your grub menu and fstab in case there were any references to "sdXX" instead of to UUIDs. The reason is at least two of the partition "sdXX" designations would change after you 'reset' them.

For those wishing to do so, here is the procedure. Note that your system will operate fine without making this change and you run the risk of screwing up your boot process or partition mounting if the partition designations no longer match in fstab or menu.lst:
```

sudo fdisk /dev/sda
```
*at the prompt:*
m [I](for help)
at the prompt:[/I]
x *(extra functionality - experts only)*
f  *(fix)*
w *(write to disk and exit)*
You may get a warning that devices are in use and the new table will be used at the next boot.  
[COLOR="DarkRed"]**Check fstab and menu.lst before rebooting.**[/COLOR]
Repeat for other drives.

Wow, thanks for the quick and detailed explanation. This is stuff that is not something I will attempt as a Newbie, especially that you were kind enough to assure me twice in response that it is not a problem and the system would operate fine as it is. For those with similar configurations and knowledge and skill to follow the posters advice, have at it, if you wish. He is obviously an expert. 

Thank you,

mikodo

---

### Post by loomsen on 2009-08-29
Hello.

Just some additional notes: 

You may only have 4 primary partitions, so if you set up your partition table with only 3 primary partitions and one of them as an extended, this will always be out of order.

Your dmesg should also show how your current set up looks like.

Basically it doesnt really matter if they're out of order, just add labels to all your partitions and you can easily access them.

Just, why the good god do you have a 8GB swap partition?

o.O

I assume your PC is quite young, so swappoff and do something useful with the space. 

It won't render your system unstable if you swap off, so you could do this live, resize the swap partition to like 1GB max, and then go for whatever comes to your mind with the freed space.

---

### Post by mikodo on 2009-08-30
> **drs305 said:**
> It is not a problem. You can "reset" them to the correct order but you would need to check your grub menu and fstab in case there were any references to "sdXX" instead of to UUIDs. The reason is at least two of the partition "sdXX" designations would change after you 'reset' them.

For those wishing to do so, here is the procedure. Note that your system will operate fine without making this change and you run the risk of screwing up your boot process or partition mounting if the partition designations no longer match in fstab or menu.lst:
```

sudo fdisk /dev/sda
```
*at the prompt:*
m [I](for help)
at the prompt:[/I]
x *(extra functionality - experts only)*
f  *(fix)*
w *(write to disk and exit)*
You may get a warning that devices are in use and the new table will be used at the next boot.  
[COLOR="DarkRed"]**Check fstab and menu.lst before rebooting.**[/COLOR]
Repeat for other drives.

Hello; It still is bothering me that my Partition table entries are not in order. Do the screenshots of my fstab and grub menu indicate that it is safe to run the above quoted code to fix them?

Thank you.

---

### Post by mikodo on 2009-08-30
Hello everyone,

I went ahead and run the above code, and now my Partition table entries are in order. Please see screenshot of same.

Thank you all.

---

### Post by drs305 on 2009-08-30
> **mikodo said:**
> Hello everyone,

I went ahead and run the above code, and now my Partition table entries are in order. Please see screenshot of same.

Thank you all.

Glad it worked out. In checking those two files, what I would have looked for is any "sdXX" entry, such as sda5, instead of the (now) expected UUIDs. If everything is referenced by UUID, then the command won't create any boot or mount issues.

---

### Post by srs5694 on 2011-05-13
> **drs305 said:**
> For those wishing to do so, here is the procedure.

FWIW, when *only* logical partitions are out of order, my [FixParts](http://www.rodsbooks.com/fixparts/) program does this automatically -- just launch the program and type "w" to save the changes. (It's always wise to verify you're working on the right disk by typing "p" to check the partitions, though. This also lets you verify that the partitioning tool has correctly read all the partitions.)

> **drs305 said:**
> It is not a problem.

I'd like to reiterate this point, and add that there's *always* a risk of damage when messing with partition tables. I know that mikodo has done the modification without problems, but an error (user error, a bug in a program, a power failure at exactly the wrong moment, etc.) can cause the partition definitions to be lost, and that will take a lot of effort to correct. It's just not worth the risk for something like this. Note that there's no "IMHO" in that statement.

> **loomsen]You may only have 4 primary partitions, so if you set up your partition  table with only 3 primary partitions and one of them as an extended,  this will always be out of order.[/quote]

Not quite said:**
> Your dmesg should also show how your current set up looks like.

The dmesg command displays the kernel ring buffer, which contains messages generated by the kernel. Mostly these relate to hardware detection and errors. Among many other things, these messages will show you how many partitions you've got and how they're numbered, but they won't say anything about partition sizes. For instance:

```

[    5.499096] sd 1:0:1:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    5.499129] sd 1:0:1:0: [sdb] Write Protect is off
[    5.499131] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.499149] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.499235]  sdb: sdb1 sdb2 sdb3

```

That last line indicates the disk has three partitions, /dev/sdb1 through /dev/sdb3. (On a disk with extended and logical partitions, that arrangement is indicated, IIRC.) There's nothing there about partition sizes or types. For such information, you've got to use a partitioning tool like fdisk, parted, GParted, or gdisk.

[quote=aj_84@live.co.uk]can you help me how to put this in order, i have three primary partition  and one extended partition. I just want to get the linux versions  together.[/quote]

Your Linux partitions are contiguous in on-disk space; the last two (your logical partitions) are just out of order in their numbering sequence. This is unimportant, and as I wrote earlier, changing your partitions just to "fix" this is inadvisable. Basically, your disk isn't broken, and there's wisdom to the saying, "if it ain't broke, don't fix it."

FWIW and for future reference, it's generally best to put a swap partition in-between Linux partitions (in terms of actual partition sectors, not necessarily the partition numbers). This minimizes head seek movements when accessing swap space, thus improving performance. Since swap space is rarely used today, though, I wouldn't advise trying to change your existing configuration; you'll spend more time trying to improve performance than you could possibly save by optimizing your swap file placement, and you'll run the risk of creating bigger problems. It's just something to keep in mind for the next time you partition a disk.

---

