---
title: "Can Live-CD or -USB be used on Mac?"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by yc2 on 2011-02-03
Hello

If I use a PC to burn a Live CD can I use that on  Mac?
If I put the live CD on a USB stick/thumb drive (still using a PC) can I use it on a Mac to f.ex. install Ubuntu?

(I am referring to modern Macs with Intel architecture)

I would also like to know the answer to the "reverse" questions. Can Live media (CD/USB) created on Mac be used on PC?

Thanks

---

### Post by coffeecat on 2011-02-03
As far as I know - yes and yes.

When you burn an ISO to CD you are burning an image to create the CD filesystem. It makes no difference what operating system or software you use to do this - the final result will be identical.

I have booted up Ubuntu on my Mac Mini from a live CD prepared in Ubuntu. I have also used the Mac OS Disk Utility to burn an Ubuntu live CD which happily booted up on a standard BIOS PC.

As far as live USBs are concerned, I'm not sure, but the story ought to be the same.

---

### Post by neofreud on 2011-02-03
Absolutely, I have done it several times but never quite comitted to putting ubuntu on my MacBook Pro. 

You can follow the steps listed [here.]("http://kb.iu.edu/data/ages.html") 

Basically the same way that a PC works, as long as it is booting first from the CD or USB then it will ignore the hard disk and viola! 

Cheers, 

Lev

---

### Post by TechWiz2100 on 2011-02-03
I think USB's may or may not boot in Leopard or higher because the OS seeks an HFS partition before it even attempts to boot from it. So you can do it with an external hard drive but not with a flash drive since partitioning those usually leads to serious issues.

---

### Post by mcduck on 2011-02-03
Live-CD is fine, but Live-USB is a bit tricky since Macs require GPT partition table to boot from a hard drive (or any USB drive). Your USB drive probably uses older MBR partitioning instead.

It should be possible to make a USB drive bootable on macs, though. But I can't tell you how easily it's done, never tried it myself (I only have one USB flash drive and prefer keeping it bootable on PC's instead)

---

### Post by quesadilla on 2011-02-03
as far as I know both can be used just fine.

---

### Post by srs5694 on 2011-02-03
> **TechWiz2100 said:**
> I think USB's may or may not boot in Leopard or higher because the OS seeks an HFS partition before it even attempts to boot from it. So you can do it with an external hard drive but not with a flash drive since partitioning those usually leads to serious issues.

This is partially speculative, but: If a limit for live USB booting on a Mac is that the Mac's EFI looks for an HFS+ partition, you could create an Ubuntu installation with a separate /boot partition and then, after installation, convert that to HFS+. I did that once on a Mac Mini and it worked fine; however, this was a test installation to a hard disk, not a USB flash drive. You could even do this all with a GPT disk rather than an MBR disk, if it would make the Mac's EFI any happier.

---

### Post by TechWiz2100 on 2011-02-03
> **srs5694 said:**
> This is partially speculative, but: If a limit for live USB booting on a Mac is that the Mac's EFI looks for an HFS+ partition, you could create an Ubuntu installation with a separate /boot partition and then, after installation, convert that to HFS+. I did that once on a Mac Mini and it worked fine; however, this was a test installation to a hard disk, not a USB flash drive. You could even do this all with a GPT disk rather than an MBR disk, if it would make the Mac's EFI any happier.

You can do all of that on an external USB Hard Disk but a flash drive is usually not partition friendly and the device will throw a few fits and tantrums when you try that (personal experience). Maybe newer flash drives are more partition friendly but my recent experience with partitions on flash drives tell me that its simply not feasible.

---

### Post by coffeecat on 2011-02-03
> **TechWiz2100 said:**
> You can do all of that on an external USB Hard Disk but a flash drive is usually not partition friendly and the device will throw a few fits and tantrums when you try that (personal experience). Maybe newer flash drives are more partition friendly but my recent experience with partitions on flash drives tell me that its simply not feasible.

That is a curious statement. What do you mean by "partition friendly"? Since they first appeared USB flash drives have been marketed already setup with mbr partition tables and at least one FAT partition. My first USB flash drive (can't remember the size; either 64 or 128MB!) came with two partitions with some Windows utility on the small one.

I've never encountered a problem creating more than one (or even just one) partition on a USB flash drive. You must have had a faulty drive.

---

### Post by TechWiz2100 on 2011-02-03
> **coffeecat said:**
> That is a curious statement. What do you mean by "partition friendly"? Since they first appeared USB flash drives have been marketed already setup with mbr partition tables and at least one FAT partition. My first USB flash drive (can't remember the size; either 64 or 128MB!) came with two partitions with some Windows utility on the small one.

I've never encountered a problem creating more than one (or even just one) partition on a USB flash drive. You must have had a faulty drive.

I mean I get issues using the device after its been partitioned and partitioning itself usually causes some kind of flunky performance. I also get the issue with a few different drives so I don't know. I remember once tryna partition my Corsair 8GB and it blatantly refused to allow me to use the 2nd partition. It would only load 1 partition even though both were "formatted" with gparted.

---

### Post by srs5694 on 2011-02-03
*Windows* has issues with partitioned USB flash drives; it insists on treating all USB flash drives as "superfloppies," and so will read only the first partition. That's a *Windows* limitation, though, not a Linux or Mac OS limitation. Since this thread is about Ubuntu on Macs and PCs, Windows doesn't really enter into it (unless Windows were being used to create the USB flash drive under discussion, but that seems unlikely since Windows would have a hard time with the Linux filesystems).

It's conceivable you'd get reduced performance on at least some USB flash drives if the partitions aren't aligned properly, much as on SATA SSD disks; however, I've not looked into this issue in any detail. I'm skeptical it would be much of an issue, since the USB 2.0 interface used by most such drives would be a more significant bottleneck than any alignment issues. I could be wrong, though.

Beyond that, there are no problems with partitioning USB drives, AFAIK. Certainly I do it frequently. (I'm the author of [GPT fdisk, aka gdisk,](http://www.rodsbooks.com/gdisk/) and I use USB flash drives as testbeds for new gdisk features, as well as for testing problems with MBR disks when I read about them.) As coffeecat says, USB flash drives frequently come from the factory pre-partitioned, albeit with a single FAT partition. There's absolutely nothing inherent to the technology that could make the drives themselves not "friendly" to partitions; partitions are just groups of disk sectors defined in a data structure, and USB flash drives, like all disks, are just tools to store data.

---

### Post by yc2 on 2011-02-03
Thanks a lot for considering many aspects of my question. (I am on a trip and can only reply irregularly, but I carefully read all you write :) )

---

### Post by TechWiz2100 on 2011-02-04
> **srs5694 said:**
> *Windows* has issues with partitioned USB flash drives

Huh, I never knew windows was so finicky about partitions on flash drives. However the last time I tried it, I attempted to use it on Ubuntu Server and I may have gotten the mount command or something wrong but it wouldn't let me mount my 2nd partition on the flash drive.

I guess I'll look into it some more. I would love it if partitioning flash drives worked flawlessly because that would make it easier to use it for lets say multi-boot flash drive

---

### Post by srs5694 on 2011-02-04
> **TechWiz2100 said:**
> Huh, I never knew windows was so finicky about partitions on flash drives. However the last time I tried it, I attempted to use it on Ubuntu Server and I may have gotten the mount command or something wrong but it wouldn't let me mount my 2nd partition on the flash drive.

If you've got reproducible problems under Linux, I'd be interested in hearing about them. I've never had such problems, though, and prior to this thread, I can't recall hearing of anybody else having them, either.

---

### Post by TechWiz2100 on 2011-02-05
I never tried a partitioned flash drive on linux because it didn't work on my PC nor my friends Mac so I assumed it to be a lost cause while partitioned. Also at the time I wasn't too up to much of a linux user.

---

### Post by srs5694 on 2011-02-05
Partitioned USB flash drives work fine for me under Mac OS X. Of course, OS X only shows the partitions that have filesystems it recognizes, so if you had a flash drive with, say, one ext3fs and one FAT partition, you'd only see the FAT partition.

---

### Post by TechWiz2100 on 2011-02-07
I believe it was 3 FAT32 partitions on Tiger just before Leopard dropped

It refused to mount at all although the disk utility (if thats what it was called at the time) showed the device.

---

### Post by srs5694 on 2011-02-07
I just tried with a 2 GB USB flash drive on OS X 10.4.11 on an Intel-based Mac Mini and it recognized and mounted all the FAT partitions (created in Linux) on a 3-partition disk. I was also able to create a disk with three FAT partitions on a 16 GB USB flash drive using Disk Utility in OS X 10.4.11, and the OS mounted those fine. Thus, I suspect that whatever you ran into was either a weird bug or a problem with the disk -- maybe your filesystems were damaged, for instance, in a way that caused OS X to refuse to mount them.

---

### Post by TechWiz2100 on 2011-02-07
> **srs5694 said:**
> I just tried with a 2 GB USB flash drive on OS X 10.4.11 on an Intel-based Mac Mini and it recognized and mounted all the FAT partitions (created in Linux) on a 3-partition disk. I was also able to create a disk with three FAT partitions on a 16 GB USB flash drive using Disk Utility in OS X 10.4.11, and the OS mounted those fine. Thus, I suspect that whatever you ran into was either a weird bug or a problem with the disk -- maybe your filesystems were damaged, for instance, in a way that caused OS X to refuse to mount them.

Interesting. I guess it was some kind of fluke then or maybe a hardware issue because I was still able to use the device after I repartitioned it to 1 FAT32 partition. Thanks for clearing that up, gunna go see if I have any large flash drives laying around to create a multiboot repair drive or something.

---

