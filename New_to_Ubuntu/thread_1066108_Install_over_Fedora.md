---
title: "Install over Fedora"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by backfour94 on 2009-02-10
Hi, I've been playing with an Ubuntu 8.10 live cd that I got on the cover of a mag in the UK.  It's all going very well I've been able to connect to my home network, sharing a printer connected to the Ubuntu PC, sharing files, accessing the internet etc.

So I decided to install as a dual boot with Windows XP as there are a couple of programs that I'd like to keep.  But I couldn't get the partitioning to work.  It kept on failing with 'an error has occured' no matter how much I compressed the disk and ran chkdsk it still failed.  

So I decided to give Fedora 10 a go.  It's no where near as clear what's going as Ubuntu but with a bit of guessing the partition program ran first time and Fedora installed.  It's connected to the internet and looks like it's on the home network.  But before I go full ahead and get used to Fedora I'd like to see if I can get Ubuntu going.

So how easy is it to install Ubuntu over Fedora?  When I run the install program it starts with the partition program which I don't think I need to run again (Fedora looks to have left the disk with the XP partition, a boot partition and a third one which must be the Linux one).

I'm very new to Unix, partitions and all that but I'm fairly good with computers generally.

Any help much appreciated, thanks.

---

### Post by Elfy on 2009-02-10
I think I read here somehwere that there were some dodgy cds on mags in the UK with a partitioning error

You can install over the top of the fedora or run all 3 if you wished - but I would download and burn the disc myself if it was me.

---

### Post by backfour94 on 2009-02-10
Thanks, but if I download a new disk how do I install over Fedora?

I presume that I'll need to chnge both the boot partition and the fedora one?

I've look but can't see any guidelines.

---

### Post by JK3mp on 2009-02-10
Quite simple. When you run Ubuntu Install just set to overwrite or reuse the partition that fedora's on. The bootloader will automatically take effect. Did with mine anywho..

---

### Post by joey-elijah on 2009-02-10
> **JK3mp said:**
> Quite simple. When you run Ubuntu Install just set to overwrite or reuse the partition that fedora's on. The bootloader will automatically take effect. Did with mine anywho..

That's pretty much bang on the buckwheat! 

It'll ask if it can erase and reuse the partition and, if you have no qualms about that, that is pretty much it.

The other option is to shrink your fedora partition and then use whatever you free up, but i'm guessing you don't to keep fedora, so the first solution is simpler.

---

### Post by backfour94 on 2009-02-11
Thanks for this folks, I'm not quite there yet.

So I boot the machine from the CD; start the install process from the desktop; answer the first few questions and the partitioner starts.

It suggests that I overwrite the whole disk which I don't want to do.  If I select 'manual' I can see the three partitions.

But how to I tell the installer to choose the right partition, i.e. the one that I want to over write?  

Thanks again.

---

### Post by Elfy on 2009-02-11
Pick the partition you want to install over - Edit partition - Use As dropdown menu - ext3 or whatever you want - Mountpoint dropdown pick / Close that window - in the partition line you wish to use - tick the format box

If you also have a seperate home then for that partition mountpoint is /home

---

### Post by kansasnoob on 2009-02-11
You first need to understand partitioning basics.

And what I want to know before going any further is if Win will still boot after installing Fedora?

---

### Post by backfour94 on 2009-02-13
> **kansasnoob said:**
> You first need to understand partitioning basics.

And what I want to know before going any further is if Win will still boot after installing Fedora?

Yep the machine currently dual boots into either Fedora or WinXP

---

### Post by backfour94 on 2009-02-13
Thanks forestpixie did that and got the install to start and it very nearly finished.

Got:

Execution 'grub-install (hd0)' failed.  This is a fatal error.

Then:

Sorry, the program "ubiquity" closed unexpectedly.  If you were not doing ....... report the problem.

I reported the problem and was directed to 260001 ubiquity crashed with InatallStepError in congigure_bootloader().

So I guess that there is a problem writing the to /boot partition.  The bug report talks about something call inode size.

Thanks to all for the help so far.  Any more greatly received.

Incidently XP still boots fine.

---

### Post by Elfy on 2009-02-13
Last time I had that error myslef it was dodgy burn - have you the link to the bug - launchpad is a pain to search.

---

### Post by backfour94 on 2009-02-13
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001)

pretty sure

---

### Post by backfour94 on 2009-02-21
This has been solved under thread:

[http://ubuntuforums.org/showthread.php?t=1070394](http://ubuntuforums.org/showthread.php?t=1070394)

Thanks very much to all that have helped me.

---

