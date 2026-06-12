---
title: "Cannot Move or Delete Some Files on External HD"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by gruurly on 2009-10-22
Relatively new to Linux. Have found other solutions WAY above my head so I thought I'd post it here.

I've got a small external HD that suddenly won't let me move or delete certain files. Not all, just a handful. I get a "Error moving file: Input/output error" whenever I try.

Help?

---

### Post by Konbuntu on 2009-10-22
i get the same problem! im trying to move a file to my desktop and it won't let me

---

### Post by Dark_Stang on 2009-10-22
Huh, only on Linux? The drive may slowly be failing or you might have some minor file system errors. You could try running a fsck (file system check) if it's a linux file system, or if it isn't a Windows file system you could run a "chkdsk /r" on it from a windows machine.

---

### Post by SirSlipALot on 2009-10-22
I had similar problems with windows partitions

---

### Post by gruurly on 2009-10-25
When I do as suggested, Terminal tells me:

laptop@laptop-laptop:~$ fsck
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

Scary stuff for a newbie.

---

### Post by LewRockwell on 2009-10-25
you can run the fsck from a LiveCD/LiveUSB *nix distro

.

---

### Post by gruurly on 2009-10-25
I'm not quite sure what this means. I need to find a .nix distro, burn it to CD and then run the command from that CD?

I'm a n00b, I need pretty basic instructions.

---

### Post by mapes12 on 2009-10-26
Applications>Terminal ```
sudo fdisk -l
```and post the output back here.

---

### Post by my_key on 2009-10-26
Thats because probably sda1 is the drive you're running ubuntu from. That one is mounted. It's just warning you that you shouldn't run it on that drive unless you're sure about it and you have backups.

But back to your problem. I'm sorry to say this but if you have input/output errors it nearly always means that the disk has damaged sectors or worse is dying. How old is it? Does it make weird noises when seeking? Better make the backup late than never.

The fact that you cannot move some files might be because they're damaged or it might be a permission problem. For the permission problem: run this command in a terminal (or in the run window after pressign ALT + F2): gksu nautilus 
(Type your password. It will open your file browser als root). Can you move the files now? You might need to go look for the external drive in your /media folder if it's not in the right hand pane.

If your files are "lost"/damaged there's other things you can try like trying spinrite, photoreq, testdisc or some other filerecovery or filecarving utilities. With these tools it might be possible to recover the "lost" files.

Check this tread for more info [http://ubuntuforums.org/showthread.php?t=1027065](http://ubuntuforums.org/showthread.php?t=1027065)

Good luck.

---

### Post by LewRockwell on 2009-10-26
> **gruurly said:**
> I'm not quite sure what this means. I need to find a *nix distro, burn it to CD and then run the command from that CD?

I'm a n00b, I need pretty basic instructions.

*nix:
[http://en.wikipedia.org/wiki/Unix-like](http://en.wikipedia.org/wiki/Unix-like)

distro:
[http://en.wikipedia.org/wiki/Distro](http://en.wikipedia.org/wiki/Distro)

[http://en.wikipedia.org/wiki/Linux_distribution](http://en.wikipedia.org/wiki/Linux_distribution)

LiveCD:
[http://en.wikipedia.org/wiki/Live_CD](http://en.wikipedia.org/wiki/Live_CD)

LiveUSB:
[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

Various:
[http://en.wikipedia.org/wiki/List_of_live_CDs](http://en.wikipedia.org/wiki/List_of_live_CDs)

Informational:
[http://en.wikipedia.org/wiki/Comparison_of_Linux_Live_CDs](http://en.wikipedia.org/wiki/Comparison_of_Linux_Live_CDs)

Sudo Silliness:
[http://store.xkcd.com/xkcd/#Sudo](http://store.xkcd.com/xkcd/#Sudo)

.

---

### Post by gruurly on 2009-10-27
sudo fdisk -l shows:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82edc8ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe470b0d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

Thanks for the links; I'll review them as I'm able.

As for the HD, the original was received last Christmas as a gift but it died not even 6 months later and was replaced under warranty. Warranty has now expired (they wouldn't extend it after receiving a replacement), and I haven't had any other issues with it although yes it occasionally does make sounds - but it has since day one. I've already started backing up my data since I'd assumed this was the start of the end too.

---

### Post by gruurly on 2009-10-27
> **my_key said:**
> For the permission problem: run this command in a terminal (or in the run window after pressign ALT + F2): gksu nautilus 
(Type your password. It will open your file browser als root). Can you move the files now? You might need to go look for the external drive in your /media folder if it's not in the right hand pane.

Thank you for the suggestion. I tried this, and I still wasn't able to move or delete the files. Its only 5 files, and I've moved and deleted newer/older ones before and since, but these 5 won't budge. 

> Check this tread for more info [http://ubuntuforums.org/showthread.php?t=1027065](http://ubuntuforums.org/showthread.php?t=1027065)

Thanks, I'll check that out now.

---

