---
title: "GRUB error: no such partition   grub rescue&gt;"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by dtom2444 on 2010-01-28
I used to dual-boot on my Sony Vaio between Windows Vista and Ubuntu 9.10. I decided to resize the two partitions using GParted.

I MADE A HUGE MISTAKE!

I accidentally deleted BOTH partitions and now have NO operating system on my hard drive. On startup, I get this GRUB error:

```
GRUB loading.
error: no such partition
grub rescue>
```

After doing some research, the only solution I could find is the set the root to the correct partition (set root=(hd0,1)). This works except for the small detail where I don't have ANY operating systems on the hard drive! Any other "solutions" I've found say to type in commands, but the only two commands I've found to work are 'ls' (to list everything in the working directory) and 'set root...', everything else gives me an "Unknown command" error.

Here's what I've tried so far:
 - Windows XP (SP2) CD
 - Ubuntu 9.10 Live CD
 - Ubuntu 9.10 bootable flash drive
 - Windows Server 2003 CD
 - Windows Vista Recovery disc

I set BIOS to load the optical drive first, and the internal hard drive last. The XP cd boots (!) and loads all the drivers and gets to the part where it prompts to press ENTER to start the installation. Then, it gives me an error about no hard drive detected.

Everything else I tried has NO affect. It stalls for a few extra seconds then goes right to the GRUB error again. 

So...what can I do??? I can't install ANY new operating systems, no Live CD's will even boot, I can create/delete partitions but what for??? 

I suspect it has something to do with GRUB and the MBR, but can't find any fix.

Thanks for ANY help in advance.

---

### Post by llawwehttam on 2010-01-28
Use Gparted or the ubuntu live cd's partition editor to format the hard drive all to ntfs. If you can't boot either of these it would suggest your HDD is starting to fail but you may be able to boot opensuse, for some reason its friendly to messed up machines. Is should be visable to OS's then. As for your data thats gone.....

---

### Post by flabdablet on 2010-01-28
There is nothing you can do to what's recorded on your hard disk that will stop an otherwise bootable live CD from being able to do so. So relax, breathe, and find a way through the twisty little maze of BIOS settings to get your machine to boot up from an Ubuntu live CD. If this proves to be impossible, the fix will involve either burning a new live CD or replacing your Vaio's CD drive, and will not affect your hard disk in any way.

Deleting partitions does not, in general, damage the data that used to be recorded in those partitions. All it does is hide that data from view to some extent. So once you've got to the point of being able to boot up from the live CD again, all you're going to need to do is (a) find out whereabouts on your hard disk the old partitions were and (b) create a new partition table that allows access to them. You will not have to reinstall either of your operating systems, and you will probably find that all your data is perfectly intact.

Relax. Breathe.

---

### Post by pathfindermwd on 2010-01-28
Well if it's any consolation I did something similar the other day, only it was the Ubuntu partitioner that had unintended consequences.  I lost my windows 7, and the ubuntu install.  I hope your issue has a solution someone here can help you with.

---

### Post by duruttye on 2010-01-28
Hey there!

I had a similar problem of an early XP install. My hard drive was formatted in ntfs with gparted, but I was unable to install XP on it.
This problem happens when you have SATA hard drive and you have RAID/SATA mode configured in BIOS. There are 2 ways of fixing this problem.

Check this out, maybe it helps:
[http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/](http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/)

no expert here,
and good luck

---

### Post by dtom2444 on 2010-01-28
> **llawwehttam said:**
> Use Gparted or the ubuntu live cd's partition editor to format the hard drive all to ntfs. If you can't boot either of these it would suggest your HDD is starting to fail but you may be able to boot opensuse, for some reason its friendly to messed up machines. Is should be visable to OS's then. As for your data thats gone.....

As I've previously stated, the Live CD's don't load, at all. No prompt or anything. Haven't tried OpenSuse yet though.

> There is nothing you can do to what's recorded on your hard disk that will stop an otherwise bootable live CD from being able to do so. So relax, breathe, and find a way through the twisty little maze of BIOS settings to get your machine to boot up from an Ubuntu live CD. If this proves to be impossible, the fix will involve either burning a new live CD or replacing your Vaio's CD drive, and will not affect your hard disk in any way.

Deleting partitions does not, in general, damage the data that used to be recorded in those partitions. All it does is hide that data from view to some extent. So once you've got to the point of being able to boot up from the live CD again, all you're going to need to do is (a) find out whereabouts on your hard disk the old partitions were and (b) create a new partition table that allows access to them. You will not have to reinstall either of your operating systems, and you will probably find that all your data is perfectly intact.

Relax. Breathe.

Yea, I figured it would have to be some setting in BIOS to get the bootable CD's to boot but the thing is there are NO such settings available.

The only BIOS settings I can change are time/date, External drive/network boot, BIOS password, and boot priority order. That's it...

> Hey there!

I had a similar problem of an early XP install. My hard drive was formatted in ntfs with gparted, but I was unable to install XP on it.
This problem happens when you have SATA hard drive and you have RAID/SATA mode configured in BIOS. There are 2 ways of fixing this problem.

Check this out, maybe it helps:
[http://www.raymond.cc/blog/archives/...your-computer/](http://www.raymond.cc/blog/archives/...your-computer/)

no expert here,
and good luck

Thanks for the great link! But, as stated above, no BIOS settings to change as the article suggests. Although, the external floppy drive bit might do the trick. I was just really hoping not to have to buy anything in the process of fixing this. 

BTW, not that interested in getting me data back. It's (mostly) all backed up.

Thanks for all the help so far. Anymore suggestions???

---

### Post by duruttye on 2010-01-28
I assume that you have another system, and I'm assuming that you can write a cdrom, too.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) - give it a try, I used it a few months back, it wasn't that complicated!

---

### Post by dtom2444 on 2010-01-28
> **duruttye said:**
> I assume that you have another system, and I'm assuming that you can write a cdrom, too.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) - give it a try, I used it a few months back, it wasn't that complicated!

Question: I found this earlier, downloaded it and burned it to another disk. But...what exactly am I supposed to do??? On start-up, the computer just ignores the disk in the cd drive as if it wasn't there. Did I do something wrong?

---

### Post by duruttye on 2010-01-28
I think it should boot up, just like the XP installation cd did, but i'm afraid this is way over my head...

someone else, maybe??

---

### Post by Leppie on 2010-01-28
> **dtom2444 said:**
> The only BIOS settings I can change are time/date, External drive/network boot, BIOS password, and boot priority order. That's it...
could you tell us the setup and options for "boot priority"?

---

### Post by vKool on 2010-01-28
> **duruttye said:**
> I think it should boot up, just like the XP installation cd did, but i'm afraid this is way over my head...

someone else, maybe??

yeah I was going to suggest Super Grub. it has some really nice features to repair grubs that have things like this happen. It should boot right into the cd (like a live cd) with a very simple GUI (very simple) make sure that your boot sequence goes to the CD drive first before the hard drive and you should be able to get into it. I have also booted Super Grub from a usb flash drive. Once there you should be able to select "repair GRUB" or a similar option.
Good luck

---

### Post by dtom2444 on 2010-01-28
The laptop is a Sony Vaio VGN-NR430E and the options for boot priority are:
```

- Internal Hard Disk Drive
- USB Hard Disk Drive
- USB Optical Drive
- USB Flash
- Internal Optical Drive
- Network
- Floppy Disk Drive

Exclude from boot order:
```

I've even tried adding the Internal Hard Disk Drive as an exclusion but then I just get another error saying "Operating System Not Found"

> **vKool said:**
> yeah I was going to suggest Super Grub. it has some really nice features to repair grubs that have things like this happen. It should boot right into the cd (like a live cd) with a very simple GUI (very simple) make sure that your boot sequence goes to the CD drive first before the hard drive and you should be able to get into it. I have also booted Super Grub from a usb flash drive. Once there you should be able to select "repair GRUB" or a similar option.
Good luck

Trying this now, thank you.

---

### Post by dtom2444 on 2010-01-28
So I put Super Grub Disk on a USB flash drive and it loads but the problem remains. It lets you choose which partition to boot from but, AGAIN, I have NO OS installed. I'm trying to find an option that lets me choose to boot from a CD to install ANY operating system. Don't see any option to just "Repair" Grub.

---

### Post by Leppie on 2010-01-28
set the boot priority to boot the cdrom first:
> - Internal Optical Drive


---

### Post by mcoleman44 on 2010-02-03
If super grub can allow you to boot to a live cd then it's probly just your master boot record that's screwed up. So if you can boot to a live cd then just download partition table doctor, put it on a cd and u can fix your mbr.

---

### Post by bilalakhtar on 2010-02-03
Yes, just as Leppie said, in the Boot Priority options, set 
```
Internal Optical Drive
```
as the first option in the Boot Priority Menu.
Then, reboot with the UBuntu 9.10 LiveCD in the drive.
If it doesn't work, set
```
USB optical drive
```
As the first option in the Boot priority menu and reboot with CD in drive again.

---

### Post by sameer.walgude on 2010-03-12
Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal

(here x represents the partition number where ubuntu is installed...)
(try ls at prompt to know your existing partitions...)

If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

