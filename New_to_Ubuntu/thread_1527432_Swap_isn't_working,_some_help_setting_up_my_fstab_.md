---
title: "Swap isn't working, some help setting up my fstab pls"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by kabal4u on 2010-07-09
I've been going through Google and the Forum for quite some time today, and few hours yesterday. And I'm utterly confused, i do believe something in the fstab file is not properly configured and despite the numerous faqs and threads on swap space and fstab I read, I cant seem to manage it...

Here's the content of my fstab file
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fbe75cb0-a635-461b-9369-41d21b33383e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=a0aae5ef-3845-4492-95a3-8ac9cb8de8f6 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=d2dfcbfd-538a-412a-9d24-2f645700d8ef       swap            swap    default	          0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 swap swap sw 0 0
```

List of the partitions I currently have:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2619    21037086   83  Linux
/dev/sdb2            2622       19457   135235139    5  Extended
/dev/sdb5            2622       18705   129194698+  83  Linux
/dev/sdb6           18706       18967     2104483+  83  Linux
/dev/sdb7           18968       19457     3935893+  82  Linux Swap / Solaris
``` 

I wish to set up /dev/sdb7 as my swap space

Results after "free -m" command
```
total       used       free     shared    buffers     cached
Mem:          2012        538       1473          0         38        258
-/+ buffers/cache:        242       1769
Swap:         3843          0       3843
kaal@Kaal-Atan:~$ sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000452fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2619    21037086   83  Linux
/dev/sdb2            2622       19457   135235139    5  Extended
/dev/sdb5            2622       18705   129194698+  83  Linux
/dev/sdb6           18706       18967     2104483+  83  Linux
/dev/sdb7           18968       19457     3935893+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0c2d0c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9728    37182442+   f  W95 Ext'd (LBA)
/dev/sda5            5100        9728    37182411    b  W95 FAT32
kaal@Kaal-Atan:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012        649       1362          0         39        297
-/+ buffers/cache:        312       1700
Swap:         3843          0       3843
```

After I try the following 'sudo /sbin/mkswap /dev/sdb7' irecieve:
```
Setting up swapspace version 1, size = 3935888 KiB
no label, UUID=d594bca0-4329-47b0-8ce3-4782362982bc
```

The UUID changes every time I try this so updating the fstab file makes no sense for me?!?

Perhaps the resolution for this is simple, but after so much information I went trough I get more and more confused. I decided it's better to ask, rather than poking around and making a bigger mess..

---

### Post by CharlesA on 2010-07-09
Not sure what it should say on a desktop install, unfortunately. I'm not sure why it has marked all of it as "shared." Do you have hibernate enabled by chance?

fstab looks fine.

By using the mkswap command, you are recreating the swap partition, which changes the UUID of it.

---

### Post by Paqman on 2010-07-09
You can use:
```
sudo blkid
```

To find the UUID of /dev/sdb7, then put that in fstab. Or you could just list it as /dev/sdb7, either way works.

---

### Post by QLee on 2010-07-09
[QUOTE=kabal4u]...The UUID changes every time I try this so updating the fstab file makes no sense for me?!?
...[/QUOTE]

If you edit the fstab with the correct UUID for swap and then enter the command sudo swapon -a, the swap should become available to the system.

[Edit] As Paqman wrote, you could also choose to use device node notation instead of UUID, I don't want you to think I mean UUID is the only way, you could also use LABEL notation if you have your partitions labeled.

---

### Post by ankspo71 on 2010-07-09
Hi,
You and I both have 2gb memory so our swaps barely get used unless something on our systems really requires alot of memory. When we run the free -m command, it registers as 0 swap used because it is using less than 1mb of swap (or none at all). If you would like to experiment/test your swap to see if it really works or not, you can try the following...

 Paste this command into the terminal to tell Ubuntu to aggressively use swap: ```
sudo sysctl vm.swappiness=100
```
The default is 60 by the way, and this command is only temporary because it will go back to the default value after a reboot. You can also change the value back to 60 if it causes any problems.

Now run a memory hungry application for a while then check your swap again. I am doing this test as I type this. I have been running GoogleEarth all along and my swap usage went from 216kb to 8,768kb (8.5mb roughly)

After you see that it works you can change it back (or reboot)
```
sudo sysctl vm.swappiness=60
```
_[Here is the link about swappiness]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")._

Hope this helps.

---

### Post by bodhi.zazen on 2010-07-09
What is the question exactly ?

When looking at fstab I can not understand what you are doing with swap.

In fstab you have swap identified as 

> # swap was on /dev/sdb5 during installation[FONT=monospace]
[/FONT]UUID=d2dfcbfd-538a-412a-9d24-2f645700d8ef       swap            swap    default	          0       0

And also 

> /dev/mapper/cryptswap1 swap swap sw 0 0

But when you list your partitions, swap is identified as sdb7

> /dev/sdb7           18968       19457     3935893+  82  Linux Swap / Solaris

Also you have a very (I would say excessively large) swap partition.

The Free command shows you are not using swap, this is because you have sufficient RAM.

So ...

1. In terms of swap partition size, I advise the size as RAM X 2 , max 1 Gb (some say max 512 Mb). If you have a laptop and use suspend, use swap = RAM.

2. Which partition is your swap partition ? Is swap encrypted ? What is the UUID of your swap partition ?

3. What are you wanting to change ?

4. Do you understand how Linux uses memory and what the swap partition is and how it functions ? In general, swap is much slower then RAM so as long as you have sufficient RAM you really do not want to sue swap. For large ram ( > 2 Gb ) Desktops I often do not use swap at all, no swap partition and a swapiness of 0.

```
sudo blkid
```

---

### Post by Paqman on 2010-07-09
> **bodhi.zazen said:**
> If you have a laptop and use **suspend**, use swap = RAM.


*cough* Hibernation, not suspend *cough*

---

### Post by kabal4u on 2010-07-09
Wow, I am a bit overwhelmed. Give some time to try all the solutions.

Just to note few things though:
- I tried to force linux into using swap by opening 8-9 Firefox windos 3-4 Chrome windows, Gimp, Synaptec few terminals some directories, but no change was noticable
- bodhi.zazen, I need to clarify why I cant use the swap, as for the other remarks you have made yes I can see that but cant figure out why the difference :? As for (1) - the size I folowed the formula it should be around the size of my ram or doubled and I have 2GB of RAM. (2) /dev/sdb7 is formated as Linux Swap and I mean to use it as swap, though I fail in doing so... Yes it's encrypted (3) I want Linux to use the swap and as for (4) I do intend to overwork the PC with some really demanding software, besides I wish to configure it at least once. I need to know how to set it up in the future since I plan to buy a laptop, need to know how to configure it there :)
- QLee, I'll try that right now
- CharlesA, no I don't have hibernate on, thanks for the other remarks 

Thanks everyone, and sorry for the delay. I finished work later though. I'll try to get this working now.

EDIT: wow it seems, with the current software I have the system cannot be strained more than 400MB of RAM usage (out of 2GB)

I somewhat fixed the fstab file, updated the UUID, to this end:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=fbe75cb0-a635-461b-9369-41d21b33383e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=a0aae5ef-3845-4492-95a3-8ac9cb8de8f6 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=d594bca0-4329-47b0-8ce3-4782362982bc       swap            swap    default	          0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 swap swap sw 0 0
```

Now the swap seems active, after turning it on, however after 'sudo swapon -a' I recieve the following, which kind of disturbs me:
```
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
```

And I really have no idea what that last line is present in the fstab file?!?

---

### Post by QLee on 2010-07-09
[QUOTE=kabal4u]...

...Now the swap seems active, after turning it on, however after 'sudo swapon -a' I recieve the following, which kind of disturbs me:
```
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
```And I really have no idea what that last line is present in the fstab file?!?[/QUOTE]

Sure, I'll take a guess at that. It's probably the block device created for that original swap you had on partition 5. You probably specified encrypted swap at some time but the block device no longer exists, just like the error message indicates.

---

### Post by NTL2009 on 2010-07-09
I found some notes I had from when I added a swap partition to my install. In order to get hibernate working for me, In addition to editing fstab, I had to:

> 
Make sure the entries in /etc/fstab match the new UUIDs. [ see my fstab archive files]

Edit the file '/etc/initramfs-tools/conf.d/resume' (sudo gedit) and updated the line that begins 'RESUME=UUID= .... ' with the new swap partition UUID. [NOTE: I got this from gparted]

Lastly, run 'sudo update-initramfs -u' to update the initrd with the new UUID.

Hope this helps - NTL2009

---

### Post by kabal4u on 2010-07-10
NTL2009, thank you I've updated it.

QLee, I've removed that line from the fstab file
```
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
```
Without further issues it would seem... and after a swapoff, swapon without trouble...

Since, I can't strain the RAM with the software I have present, I made it Hibernate. This also went fine, indicating the correct UUID corresponding to my swap partition.

All that is left, to do is note the useful info I found so far and everyone's advise, for further usage if I have trouble setting that up in the future.

My thanks for the quick and comprehensive replies :)

---

