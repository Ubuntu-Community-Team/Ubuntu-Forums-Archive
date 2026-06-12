---
title: "Can't get grub to boot (hd1) in external encloser."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by ranch hand on 2009-02-26
I have an external enclosure for 2 HDDs.  I have 2 WD 320Gb SATA HDDs in it.  I am trying to make a sampler of linux flavors that I can carry and use on other computers.  This works fine on my one HDD enclosure.

The idea is to have 64b installations on one HDD and 32b on the other.  I can update the 64b stuff on my box and use the Dreaded Mother In Laws box for the 32b stuff.

I have Hardy64 and UE64 on sda (hd0).  I have just installed Mepis 7 (yes I need to upgrade) on sdb.

I boot from Hardy but when I install a flavor I install grub on that partition and then set grub back to work from Hardy when everything works on the new flavor.  I was surprised when I finished installing Mepis that my normal grub menu (2 flavors) came up.

I got the information from the Mepis partition for booting it and put this in my grub menu.  I know this is good because I have it installed elsewhere  and it boots fine with the same file.  Reboot, menu comes up, point to Mepis, error - disk does not exist.  On the command line for grub I get the same message when I try;
```

grub> geometry (hd1)

```

From the Hardy Live CD I run grub and get the same thing I get when I try it from Hardy, where I am now;
```

slade@booty-desktop:~$ sudo grub
[sudo] password for slade: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd0,5)
 (hd1,5)
grub> 

```

Grub can find (hd1) so it must exist.  I have run the rest of that sequence (root and setup) to get grub to boot from (hd0,0) (Hardy) and (hd1,5) (Mepis).  Grub acts fine in terminal and acts the same for either choice.  When I reboot it is always from Hardy and the same message that the disk does not exist comes up if I try to boot to Mepis.

I have one extended partition on sdb with a small swap partition at the "right" end (sdb5) and a 42Gb ext3 partition with Mepis on the "left" end (sdb6).

The new (Mepis) partition mounts on my desktop here on Hardy at boot along with the partition on this drive (sda) for UE.

Anyone out there have a clue as to what I should do here?  I am flumuxed.

---

### Post by Xiong Chiamiov on 2009-02-27
Grub can be quite annoying sometimes, especially when dealing with order of disks.

One tool that I find helps quite a bit is [Super Grub Disk](http://supergrubdisk.org).  It allows you to, among other things, boot directly into certain partitions and modify your grub.lst easily.

You might also look into [persistent naming](http://wiki.archlinux.org/index.php/Persistent_block_device_naming).  It allows you to assign a label to a partition, then use that in your fstab, so you don't have to change anything when you reorder your drives.

---

### Post by ranch hand on 2009-02-27
WoW, I even have one of those, just never use it. Imay have to give that a whack.

I have been thinking about this problem and I was wondering if the jumper setting makes much difference on these Sata drives.  It says on the label that slave/master jumper settings are not required and gives a setting for PUIS (pins 3+4) but they are all set on 1+2 (factory setting).  I am still trying to find out what the other combos are for.  The pins are there, they must b for something.

I have no idea why but I have never labeled a drive, let alone a partition.  I didn't even realize that you could.  I would think that this would complicate things if you resize or change the number of partitions.  Something else to look into.

Probably something else I can get into trouble with.  I am real good at that.

---

### Post by ranch hand on 2009-02-27
I did try Super Grub disk.  I don't know if i am to dumb to use it or what.

I got the bugger for a backup boot system but I have had it in my drive twice and had bad results.

The first time I just looked around in it and thought it was cool.  Then I pulled it and when the box rebooted My intire grub system was screwed.  Got that straight by running the box on LiveCD and reinstalling grub.

This is the second time.  Not so bad.  Just does not recognise the USB external at all.  I am pretty sure it exists, I am on it now.

I think I am going to try installing Hardy on that partition and see if it will boot.

---

### Post by ranch hand on 2009-02-28
I don't think this is going to work.  I deleted all partitions and redid each HDD with cfdisk, flagging each as bootable.  Each contains 1 extended partition.

Put apartition on each, installed Hardy on sda and Mandriva on sdb.  No getting Mandriva to boot.

Deleted that partition and made a smaller one on sdb and asmaller one yet on sda.  Installed Mandriva with root/boot on sda and home on sdb.  This works fine and I should be able to put six flavors on twice (one 32 and one 64).

---

