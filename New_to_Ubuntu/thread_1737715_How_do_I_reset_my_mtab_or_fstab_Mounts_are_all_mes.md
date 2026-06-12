---
title: "How do I reset my mtab or fstab? Mounts are all messed up."
date: 2011-04-23
forum: New to Ubuntu
---

### Post by brnetonboy on 2011-04-23
I'm having trouble mounting a third drive, and apparently all my mount settings and mtab/fstab stuff are totally messed up. I have no idea how they work, but someone on [this thread]("http://askubuntu.com/questions/36530/ide-drive-wont-mount") told me to "reset" and try mounting again.

How do I reset my mtab? Can I just delete it? :-k

---

### Post by JKyleOKC on 2011-04-23
The /etc/mtab file is created and maintained automatically by the mount program; it only reflects the current list of mounted devices. Changing it might make matters worse but definitely will not help at all. The critical file for mounting is **/etc/fstab** and you should post it here, and tell us what you are seeing that's convinced you everything is messed up. We can then probably tell you how to put things right again.

When you post the fstab content, copy it from the screen and paste it into a reply. Then highlight all of the material you just pasted in, and click the "#" icon on the toolbar at the top of the reply dialog to surround it with "code" tags. This will preserve the formatting and make it much easier for us to read.

It may help, also, to post the output of the "sudo fdisk -l" command (that's a lower-case L, not the numeral one) so that we can correlate the entries in fstab with the identities of your disks/partitions.

---

### Post by brnetonboy on 2011-04-23
Here is my fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=87486d4a-aad3-4314-8d33-2ed4299985fa none            swap    sw              0       0
```

>  tell us what you are seeing that's convinced you everything is messed up.

I think everything is messed up based on the response in the other forum that I linked to in my original post. I don't know enough about all this to be able to see a fstab and know what looks normal or messed up.

Here's my "fdisk -l" output:


```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f7d3f7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e88d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4661    37431296   83  Linux
/dev/sdb2            4661        4866     1648641    5  Extended
/dev/sdb5            4661        4866     1648640   82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

---

### Post by oldfred on 2011-04-23
Did you just plug in your 40GB drive to install. It has sda1 as mount point but now sda1 is windows NTFS partition and sdb1 is your linux partition.



Much better to use UUIDs.

To see your UUIDs.

sudo blkid

You want the UUID of your sdb1 Linux partition.


# modify fstab to mount directory
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a


Then change fstab from this:
/dev/sda1       /               ext4    errors=remount-ro 0       1

to this note style of swap:

UUID=put uuid here        /               ext4    errors=remount-ro 0       1

Be sure to do the mount -a, if it returns no errors you have done it correctly. If it has errors re edit. Do not reboot unless you have no errors.

---

### Post by brnetonboy on 2011-04-23
> **oldfred said:**
> Did you just plug in your 40GB drive to install. It has sda1 as mount point but now sda1 is windows NTFS partition and sdb1 is your linux partition.

The 40GB is my primary drive, it's where Ubuntu is installed. I don't know what you mean by saying sda1 is now Windows NTFS. That is probably the 250GB drive... how'd that get mixed up? 

> **oldfred said:**
> 
Much better to use UUIDs.

To see your UUIDs.

sudo blkid

You want the UUID of your sdb1 Linux partition.


# modify fstab to mount directory
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a


Ok... what exactly are you telling me to do here? What do I do with that bit of code? I don't understand how fstab or any of this really work.

Thanks so much for your help though. I just need a little more details on how to go about doing this!

---

### Post by oldfred on 2011-04-23
Post this and I can give you the exact line to add. UUIDs are unique identifiers for a partition, so it will not matter if your system sometimes boots one drive as sda and then boots it sdb next time which seems to be happening to you. Is one drive SATA and another PATA?

sudo blkid

---

### Post by brnetonboy on 2011-04-23
```
/dev/sda1: LABEL="Beowulf" UUID="E2CC780BCC77D86D" TYPE="ntfs" 
/dev/sdb1: UUID="a504f8d1-3703-4056-a8cb-3e6c3f1645c6" TYPE="ext4" 
/dev/sdb5: UUID="87486d4a-aad3-4314-8d33-2ed4299985fa" TYPE="swap" 
/dev/sdc1: LABEL="FreeAgent Drive" UUID="6EDE9F49DE9F090B" TYPE="ntfs" 

```

Two are SATA (the 40GB and the 203GB) and the other is IDE.

---

### Post by oldfred on 2011-04-23
In your fstab replace this:
/dev/sda1
with this:
UUID=a504f8d1-3703-4056-a8cb-3e6c3f1645c6

use these commands:
# modify fstab to mount directory
```
gksudo gedit /etc/fstab
```# remount from updated fstab
```
sudo mount -a
```or final fstab should look like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]UUID=a504f8d1-3703-4056-a8cb-3e6c3f1645c6 [/COLOR]      /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=87486d4a-aad3-4314-8d33-2ed4299985fa none            swap    sw              0       0
```

Sometimes with mixed IDE & SATA BIOS does not bring the drives up in the same order.

---

### Post by JKyleOKC on 2011-04-23
I'll defer to oldfred so far as giving the details for making it work, but will try to answer your question as to how things got mixed up. The Linus boot routines assign arbitrary names to drives, in the sequence in which they are detected at boot time. That's where the "sda" and "sdb" labels come from -- there's nothing on the drive itself to indicate that. Way back when, that worked pretty well since all drives were a bit slow to respond and there weren't many situations where two drives would race each other to respond.

However nowadays, drives respond much more rapidly, and also the boot process has been sped up in a way that makes such a "race condition" almost guaranteed to happen -- and sometimes one drive wins to become sda, and sometimes the other!

That's why the code that oldfred is going to give you will use the "UUID" label to identify which drive is which, replacing the use of sda or sdb since these labels cannot be depended on. It's nothing that you did, just one of the little gremlins that sometimes pops out of code to make unexpected things happen.

Hope this helps you understand what's happening. As mentioned in an earlier reply, the terminal command "mount" without any modifiers following it is much better at telling you what is going on, than is viewing the "mtab" file. However, after you correct the fstab data I think both will give the same result.

---

### Post by brnetonboy on 2011-04-23
Worked beautifully! Thanks so much, all my drives are mounted properly now. I haven't rebooted yet, but I have a feeling that this will fix it for now!

Followup question: I have one of those hard drive caddys that lets you swap out drives, and I'm thinking of moving this drive (the one we just got working) into that caddy. Will the UUID that we just did get confused if I do that, or is this drive going to be set now, no matter where I put it?

Also, if I swap out drives in the caddy, I'm assuming it may get confused again, but that if I set the fstab with the UUID of each drive, that it won't be confused anymore. 

Thanks for the help!:D

---

### Post by Hedgehog1 on 2011-04-23
UUID are more likely to work when in the caddy, as you don't really need to worry about drive order.

HOWEVER grub can have issues if a key drive it depends upon is not present in the PC at boot time.

If you have each hard drive setup to boot completely Independently (you select a boot drive using a bios select every time) then you can mix and match hard drives until you run out of money.

***The Hedge***

:KS

---

### Post by oldfred on 2011-04-23
Many users create hard drives or bootable full install on flash drives and boot on multiple systems. The main issue nowadays is video drivers. If you install the proprietary drivers and the other system is different it will not work, but there are workarounds.

---

