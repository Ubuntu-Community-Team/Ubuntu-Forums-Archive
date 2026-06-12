---
title: "Partitioning Help"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by cath0dez on 2010-10-13
I just freed up some space from my OS X install and want to partition it for use by Ubuntu.  Should I set it up as an extended partition or another primary (I assume either would be ext4)?

Thanks for the input.  I included a gparted screenshot for reference.

---

### Post by drpjkurian on 2010-10-13
It can be an another primary partition. But there can be a maximum of three primary partition if I am not wrong

You can visit the blog of psychocats for partitioning tutorials

---

### Post by Elfy on 2010-10-13
4 primaries - includes extended.

I would always set it up as extended - just incase you ever needed a primary.

---

### Post by mathgeek2000 on 2010-10-13
> **cath0dez said:**
> I just freed up some space from my OS X install and want to partition it for use by Ubuntu.  Should I set it up as an extended partition or another primary (I assume either would be ext4)?

While I don't think GUID Partion tables limit you to 4 Primary Partitions (or at most 3 and an extended) I would do this for simplicity:
  sda1: EFI 
  sda2: HFS+ (OSX)
  sda3: ext4 (Linux)
  sda4: Linux-swap

Also I would use rEFIt to select between OSX & Ubuntu. Install rEFIt first (before the Ubuntu Install) that makes it easier to boot off the CD.

When you set up Grub 2 add:
  DISABLE_OS_PROBER = TRUE

to \etc\default\grub

That's basically how I set up Linux Mint, and It works well.

---

### Post by srs5694 on 2010-10-13
That disk is clearly a GUID Partition Table (GPT) disk. GPT does away with the distinction between primary, extended, and logical partitions, so you don't need to worry about that issue.

Broadly speaking, you can either move and /dev/sda4 to fill the newly-freed space or create a new /dev/sda3 in the available space and mount it somewhere convenient for Linux. Personally, I'd do the latter, since it's safer and quicker; and I'd mount the new space as /home. This will require you to move your existing /home/username directory to the new space, which entails jumping through a few hoops, but it's not too tough. (There are lots of Web-based tutorials on this sort of thing; try a Web search to find one.) In outline, from an emergency boot disc, you'd mount /dev/sda4 (say, to /mnt), rename /mnt/home to something else (say, /mnt/oldhome), create a new empty /mnt/home directory, and create a /mnt/etc/fstab entry to mount /dev/sda3 (or its filesystem UUID value, once you've created it) to /home. You'll then mount /dev/sda3 to /mnt/home and copy /mnt/oldhome/username to /mnt/home/username, where "username" is your username. Use "cp -a" or tar to do the copying, in order to preserve user ID and permission information.

One issue that may rear its ugly head is [hybrid MBRs.](http://www.rodsbooks.com/gdisk/hybrid.html) Most Macs that run Linux seem to be set up using hybrid MBRs; however, GParted replaces the hybrid MBR with a conventional protective MBR. A protective MBR is actually safer than a hybrid MBR, but changing it could cause boot problems or could cause your Linux video to become impaired. You could use [GPT fdisk](http://www.rodsbooks.com/gdisk/) rather than GParted to create a new partition, which should preserve your existing hybrid MBR but will require creating a filesystem on the new partition manually (with mkfs); or you could use GPT fdisk or gptsync to create a new hybrid MBR after you use GParted to create the new partition. Alternatively, you could go with a straight-GPT setup and try to get it to boot properly that way, but this approach seems to be poorly documented.

---

### Post by Elfy on 2010-10-13
> **srs5694 said:**
> That disk is clearly a GUID Partition Table (GPT) disk. GPT does away with the distinction between primary, extended, and logical partitions, so you don't need to worry about that issue.

Could you elucidate on that - looks like a normal view to me ... 

> **srs5694 said:**
> GPT does away with the distinction between primary, extended, and logical partitions, so you don't need to worry about that issue.I can dig that out myself I hope 

Thanks.

---

### Post by srs5694 on 2010-10-13
> **forestpiskie said:**
> [quote=srs5694]That disk is clearly a GUID Partition Table (GPT) disk. GPT does away with the distinction between primary, extended, and logical partitions, so you don't need to worry about that issue.Could you elucidate on that - looks like a normal view to me ...[/QUOTE]

The screen shot shows four partitions, /dev/sda1, /dev/sda2, /dev/sda4, and /dev/sda5. None of these is an extended partition. On an MBR disk, it's possible to have four primary partitions, but they'd be numbered 1-4; it's not possible to have /dev/sda5 as a primary partition; that number *always* refers to the first logical partition. Therefore, if this were an MBR disk, /dev/sda5 would be a logical partition and one of the others would have to be an extended partition to contain it. This isn't the case, though, so the disk *cannot* be an MBR disk.

/dev/sda1 is marked with the "EFI" label, has a FAT32 filesystem, and has the "boot" flag set. This is all normal on a GPT disk, as viewed from GParted; the EFI System Partition, which is present on all Intel-based Macs and most or all other EFI-based systems, looks like this. Furthermore, the original post mentions OS X, which normally runs on Macs, which normally use GPT disks. (Older PowerPC-based Macs use APM disks, but that's another kettle of fish....)

It's conceivable you could get an APM, BSD, or other disk type to look like that in GParted, but not an MBR disk; and on an Intel-based Mac (or even a Hackintosh), it's implausible that you'd use anything but GPT or *maybe* MBR. Thus, this is clearly a GPT disk, not an MBR disk.

---

### Post by cath0dez on 2010-10-13
Success - I created a primary ext4 partition (it was giving errors when I tried to set up an extended) and used pysdm to set up the mount on boot and permissions.

*I already was use rEFIt - not sure anything compares for dual booting to OS X.

Thanks for the help.

---

### Post by srs5694 on 2010-10-13
Unfortunately, some libparted-based tools give the impression that you can create extended and/or logical partitions on GPT disks. This is just plain bogus -- poor user interface design at best, or a bug at worst. GPT partitions aren't really primary, extended, or logical, since those are MBR concepts, although all GPT partitions are more like MBR primary partitions than they are like other MBR partition types.

---

