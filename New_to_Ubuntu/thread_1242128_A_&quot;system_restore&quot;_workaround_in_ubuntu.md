---
title: "A &quot;system restore&quot; workaround in ubuntu?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by pavan115 on 2009-08-16
:KS Hi everyone,

I've recently started using ubuntu and I've made quite a few tweaks and changes to suit my preferences in ubuntu. I don't make any extreme changes but I like to experiment with a few features here and there - and it usually ends up making the system unusable - so I have to reformat my partition with a live CD.

So I was wondering - is there a way we can go back in time before we made certain changes like the "system restore" feature in XP? (This has saved me countless times when I messed up XP). If not what would you do to undo your mistakes in linux?

Thanks!

---

### Post by rraj.be on 2009-08-16
You can backup your system volume alone locally. Its will take at-most about 5-6 GiB.

Then you can restore it when required.

There are many tools available for this like rsync.

A small search in forums should help you a lot.

---

### Post by JC Cheloven on 2009-08-16
Yeah, many of us run into the same problem again and again :-)

I'd suggest to use fsarchiver. It supports ext4, ntfs... is smart enough to archive your filesystem in a compact way, and restoring it in a partition of different size... Just google around. It comes with SystemRescueCD, by the way.

So, 
1) bring your system to an updated and functional state that you like. 
2) Archive your FS. 
3) Mess around 'till the system gets unusable.
4) Restore your archived FS.
5) GoTo 3)

Cheers :-)

---

### Post by drs305 on 2009-08-16
I use fsarchiver on the SystemRescuecd as well, having moved away from PartImage when I went to an ext4 filesystem. Actually, I've installed the SystemRescueCD files on a partition so I don't even need the CD. I reboot and select SRCD, mount the backup file partition, then run a single command to back up my / partition to the backup location.

It makes a complete copy of my working / partition, and it can be restored to a partition that isn't even the same size as the original if necessary. The backup takes about 15 minutes to run on my system, but it depends a lot on the amount of compression you use.

---

### Post by pavan115 on 2009-08-17
wow...intersting ideas :) thanks you all!

---

### Post by BobJam on 2009-08-17
> **pavan115 said:**
> I've recently started using ubuntu and I've made quite a few tweaks and changes to suit my preferences in ubuntu. I don't make any extreme changes but I like to experiment with a few features here and there - and it usually ends up making the system unusable - so I have to reformat my partition with a live CD.

So I was wondering - is there a way we can go back in time before we made certain changes like the "system restore" feature in XP? (This has saved me countless times when I messed up XP). If not what would you do to undo your mistakes in linux?That's **EXACTLY** my situation, what I do, and what I want to do.  Well put!

> **rraj.be said:**
> You can backup your system volume alone locallyThat's the same as backing up the whole OS in Windows, right?  And the restore is bootable?

> **rraj.be said:**
>  Then you can restore it when required.And I assume it would be bootable?  Or does that depend on the package you use to do it, and the method you use?  I don't want data backups (I have mine on removable media) . . . I want an OS backup that's bootable and can be restored as such, to include the exact settings and apps I had in it before I messed it up . . . IOW, a Windows restore as the OP explained.

> **rraj.be said:**
>  There are many tools available for this like rsync Downloaded and installed rsync (Synaptic Package Manager).  Will it do as I want as I explained above?  (That is, of course, if I choose to use rsync instead of fsarchive.)

Can/Should I carve out a logical partition for this from my existing DATA partition?  (I have plenty of free space on that partiton . . . well in excess of 5GB).  Would I use gparted for that and do I need to make the partition beforehand?  (I assume so if I want to store the archive on it).  What would be the "source" and "destination" directories I would put in to rsync?  And since my scenario assumes a new empty partition for storage, how would I designate that as "destination" . . . the sda path?

> **JC Cheloven said:**
> Yeah, many of us run into the same problem again and againGood to know it's not just us noobs.

> **JC Cheloven said:**
> I'd suggest to use fsarchiverI didn't see a deb package on their page, so I just burned the SRCD iso to CD and got it that way.  But then how would I run it?  From the SRCD CLI?  What commands would I use?  The ones detailed here:  [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) ?

And I have the same questions I did for rraj.be:  Will it make the restore OS bootable . . . IOW, again, does it do the same thing as the Windows Restore?  And do I need to carve out a seperate partition beforehand?

> **JC Cheloven said:**
> 1) bring your system to an updated and functional state that you like.
2) Archive your FS. 
3) Mess around 'till the system gets unusable.
4) Restore your archived FS.
5) GoTo 3)Nice flow outline, but I need more detail on #2 and #4 . . . or would that just be the instructions on [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) ?

> **drs305 said:**
> Actually, I've installed the SystemRescueCD files on a partition so I don't even need the CDJust exactly how did you do that?  Did you just copy over all the files on the CD with your file browser?.  To a separate partition dedicated to SRCD?

> **drs305 said:**
> I reboot and select SRCDSo, "SRCD" shows up on a grub menu?

> **drs305 said:**
> mount the backup file partitionWith your file browser?

> **drs305 said:**
> then run a single command to back up my / partition to the backup location.And what would that command be?

Sorry for so many questions, but I'm definitely not confident unless I know EXACTLY what I'm doing.  And as you can see, clearly I'm not confident . . . curse of the noob.

TIA

---

### Post by mapes12 on 2009-08-17
I just wrote a Howto for deploying Partimage using the System Rescue CD. It's here: [http://ubuntuforums.org/showpost.php?p=7800125&postcount=11](http://ubuntuforums.org/showpost.php?p=7800125&postcount=11)

Hope it answers some of your questions, particularly about mounting a drive when running Linux in memory. This confuses the heck out of everybody.

---

### Post by kpkeerthi on 2009-08-17
[http://backintime.le-web.org/]("http://backintime.le-web.org/")
[http://flyback-project.org/]("http://flyback-project.org/")
Both are GUI frontends to rysnc + hardlinks.

---

### Post by BobJam on 2009-08-17
> **mapes12 said:**
> I just wrote a Howto for deploying Partimage using the System Rescue CD. It's here: [http://ubuntuforums.org/showpost.php?p=7800125&postcount=11](http://ubuntuforums.org/showpost.php?p=7800125&postcount=11)

Hope it answers some of your questions, particularly about mounting a drive when running Linux in memory. This confuses the heck out of everybody.Thanks.  A lot of reading material.  Will digest it and report back.

> **kpkeerthi said:**
> [http://backintime.le-web.org/](http://backintime.le-web.org/)
[http://flyback-project.org/](http://flyback-project.org/)
Both are GUI frontends to rysnc + hardlinks.Thanks.  Likewise a lot of reading material.  Will digest it and report back.

For now . . . my head hurts . . . I think I'll take a break.

Thanks again to you and mapes 12.

---

### Post by drs305 on 2009-08-17
> **BobJam said:**
> Just exactly how did you do that?  Did you just copy over all the files on the CD with your file browser?.  To a separate partition dedicated to SRCD?
You create a partition, make two directories: sysrcd and isolinux, and copy the SystemRescueCD files into the appropriate locations. The instructions can be found: [here]("http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk")

> So, "SRCD" shows up on a grub menu?
No, I created an entry in Grub 2 that points to the SystemRescueCD partition I created. You can see an example of the menuentry I created in the "41_custom" section of the grub.cfg example on this page: [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

> 
With your file browser? And what would that command be?
From the LiveCD, I mount the partition with my backup files and a copy of fsarchiver on it ([noparse]sda8[/noparse]) with the following command:
```

mkdir /mnt/temp
mount /dev/sda8 /mnt/temp

```
The exact command I normally use to backup the system partition (sda2) is the following (it depends on the compression I want). Read up about fsarchiver to learn about the various switch options:
```

/mnt/temp/fsarchiver savefs -z 3 -v /mnt/temp/system-backup-DATE.fsa /dev/sda2

```

The restore command I use is:
```

fsarchiver restfs /mnt/temp/system-backup-DATE.fsa id=$ID,dest=/dev/sda2

```

---

### Post by asmoore82 on 2009-08-17
You may want to check out Clonezilla [http://clonezilla.org/](http://clonezilla.org/) .

---

### Post by JC Cheloven on 2009-08-21
> **BobJam said:**
> 
Nice flow outline, but I need more detail on #2 and #4 . . . or would that just be the instructions on [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) ?

Yes, personally I use fsarchiver the simple way: from command line interface (CLI) at live systemrescuecd. And I save and restore from an external usb disk. 

> Sorry for so many questions, but I'm definitely not confident unless I know EXACTLY what I'm doing.  And as you can see, clearly I'm not confident . . . curse of the noob.
TIA
Don't worry... but you'll find out soon that looking for absolute certitude is a suboptimal approach. With a bit of knowledge, with the "search-and-try-and-mess-and-undo" one, you'll learn more quickly and more pleasantly ;-)

---

### Post by sumeshgupta on 2009-08-21
you may check [www.geekconnection.org/remastersys/capink.html]("http://www.geekconnection.org/remastersys/capink.html")

---

### Post by Arquis on 2009-08-21
I personally enjoy using QUICKSTART ([http://www.quickstart.freeforums.org](http://www.quickstart.freeforums.org)). It's simple, fast, it compresses files and is a snap to recover things (it compresses the entire system or just your HOME folder). The drawback is it needs a GUI (I think it doesn't work with terminal), but the worst I had to do was to reinstall Ubuntu to have the GUI back (hardly a problem - Ubuntu install is snappy) and then I recovered the old system by running Quickstart on top of it. It is also great to fastrack a new system install with the changes you like to do every time (Remastersys does that, but I had some problems with it).

I also enjoyed GRSYNC a lot (a simple GUI for RSYNC - I prefer it to the terminal) and BACK IN TIME seems nice, but I haven't tested it yet. I use GRSYNC to make fast directory backups to my USB drive, so I can work anywhere. RSYNC (and GRSYNC) is good because it is incremental. Quickstart isn't.



Hope I helped. =)

---

### Post by Stosskraft on 2009-10-16
I just found this: [http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)

Seems closest to "system restore" I will give it a go before I try to get my 5.1 sound working.:)

---

### Post by BobJam on 2009-10-16
See these two posts of mine:
[INDENT][http://ubuntuforums.org/showthread.php?t=1288080](http://ubuntuforums.org/showthread.php?t=1288080)

[http://ubuntuforums.org/showthread.php?t=1288083](http://ubuntuforums.org/showthread.php?t=1288083)
[/INDENT]

---

