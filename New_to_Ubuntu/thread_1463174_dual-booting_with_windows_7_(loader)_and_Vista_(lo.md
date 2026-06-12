---
title: "dual-booting with windows 7 (loader) and Vista (loader)"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-26
Ok, so before I had a question regarding duel-booting with windows 7 and everyone was very helpful and thank you BUT, now I have another problem.  I had vista before and did the Windows 7 upgrade so now I have both Vista and Windows 7.  I tried to do the automatic partition resizing but that's not even an option. My options are:
1) uninstall windows 7 (loader) and vista (loader) in replace with Ubuntu 9.10
2) manually partition hard drive

Ok, so here is what I have
I have a 219G C: with 83 G free
and a 12.9 G D: (HP RECOVERY) with only 1.71 free

What can I do in order to still duel-boot and keeping my Windows 7 files and also run Ubuntu? Please let me know and thank you for your time!

---

### Post by arrrghhh on 2010-04-26
Do you have any unpartitioned or RAW space?

If so, slice that off and use Ubuntu for it...

I doubt you do however, you probably have all the hard drives fully partitioned - IE no free, unpartitioned space.

I personally had issues resizing my NTFS drives with gparted (perhaps this has changed recently, it was 2 years ago I was trying to resize ntfs with gparted...) so I always ended up using something like EASUS's partition tool.  Partition Master, free for home use.

That way I could resize my NTFS partitions to provide some RAW, unpartitioned space.  Just go back to Ubuntu start install over again, and have it use that newly created free space.

---

### Post by nitstorm on 2010-04-26
> **arrrghhh said:**
>  I always ended up using something like EASUS's partition tool.  Partition Master, free for home use.

That way I could resize my NTFS partitions to provide some RAW, unpartitioned space.  Just go back to Ubuntu start install over again, and have it use that newly created free space.

+1 for that, I toyed around with EASEUS before I put in Ubuntu too :D

---

### Post by joenewtzie on 2010-04-26
What about just installing Ubuntu through windows?

---

### Post by arrrghhh on 2010-04-26
> **joenewtzie said:**
> What about just installing Ubuntu through windows?

I was going to suggest WUBI, but the OP seemed to want to install Ubuntu on it's own.

There are some advantages, and disadvantages to WUBI.  It's really just to check-out Ubuntu, I wouldn't recommend running it full-time - reason being, is a lot of people have dual-boot so if something does get borked with Windows they still have a usable system to boot into... With WUBI, this advantage disappears.

That, and the general performance hit make it not so appealing unless you're just experimenting with Ubuntu.

---

### Post by joenewtzie on 2010-04-26
And another problem is that the EASEUS Partition Master Home Edition is not compatible with Windows 7 64 bit systems...another other recommendations?

---

### Post by arrrghhh on 2010-04-26
> **joenewtzie said:**
> And another problem is that the EASEUS Partition Master Home Edition is not compatible with Windows 7 64 bit systems...another other recommendations?

The demo for the pro version does support 64-bit, but I'm not sure how limited their demo's are...

Other alternatives would be other partition resizing tools, but I don't know how many you would want to trust with resizing your NTFS partitions.  Could cause some horrible consequences...

With that said, if you don't mind paying - PartitionMagic is what I used to use before I found EASEUS.

Obviously you could reinstall Win7 with proper partitioning, but since you have an upgrade copy that may be quite painful.

---

### Post by Arla on 2010-04-26
Doesn't windows 7 allow you to resize? I thought that was functionality built into Windows 7 itself?

---

### Post by arrrghhh on 2010-04-26
> **Arla said:**
> Doesn't windows 7 allow you to resize? I thought that was functionality built into Windows 7 itself?

Quick google search turns up [this](http://www.killertechtips.com/2009/05/05/how-to-resize-partitions-in-windows-7/) guide...

Didn't even think about that, thanks Arla!  (& thank you Google :D)

BTW, OP, I'd give yourself a minimum of 10gb to Ubuntu.  20 if you're feeling generous and can spare it :)

---

### Post by joenewtzie on 2010-04-26
> **Arla said:**
> Doesn't windows 7 allow you to resize? I thought that was functionality built into Windows 7 itself?

I'm not totally sure on that one, I'll start looking around though!

---

### Post by joenewtzie on 2010-04-26
Ok, I think I found it, its just called Disk Management, trying to figure out how to use it though...

---

### Post by joenewtzie on 2010-04-26
So do NOT use the Windows partition program? 
I just found this though 
([http://windows.microsoft.com/en-us/windows-vista/Create-and-format-a-hard-disk-partition](http://windows.microsoft.com/en-us/windows-vista/Create-and-format-a-hard-disk-partition))

---

### Post by arrrghhh on 2010-04-26
> **joenewtzie said:**
> So do NOT use the Windows partition program?

So did you miss my post or are you ignoring it?

:confused:

---

### Post by wilee-nilee on 2010-04-26
> **joenewtzie said:**
> Ok, I think I found it, its just called Disk Management, trying to figure out how to use it though...

It is easy just right click on the partition hit shrink then it will see how much it can be shrunk then accept it or pick a less amount to be shrunk. 1st though you want to defragg with a optimizer like auslogics that will move everything to the start of the disc.
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)

Also I am sure your aware that since you upgraded vista is not legal anymore.

---

### Post by LewRockwell on 2010-04-26
followed this just a few days ago on Windows 7 64-bit 320GB hard-drive with total success.

[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

.

---

### Post by joenewtzie on 2010-04-26
> **arrrghhh said:**
> So did you miss my post or are you ignoring it?

:confused:

Well, I saw that you said to not do that BUT then you said to allocate 20 GB of space for Ubuntu...so now I am confused...

---

### Post by arrrghhh on 2010-04-26
> **joenewtzie said:**
> Well, I saw that you said to not do that BUT then you said to allocate 20 GB of space for Ubuntu...so now I am confused...

This is what I said:
[quote=arrrghhh]Quick google search turns up this guide...

Didn't even think about that, thanks Arla! (& thank you Google )

BTW, OP, I'd give yourself a minimum of 10gb to Ubuntu. 20 if you're feeling generous and can spare it[/quote]

Never said not to do... well anything really.  In fact, I encourage you to use the tool within Windows to do it, in theory it *should* be the best for the job.  I just didn't realize 7 could do that, because XP certainly can't!!  Learn something new every day.

The space recommendations were just that - recommending you give at a minimum 10GB to Ubuntu, but if you're feeling generous or have the space to spare 20GB would be better...

---

### Post by joenewtzie on 2010-04-26
Ok awesome, i'm working on getting 20G free now..Sorry for that though, I have so much going on right now!

---

### Post by joenewtzie on 2010-04-26
> **LewRockwell said:**
> followed this just a few days ago on Windows 7 64-bit 320GB hard-drive with total success.

[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

.

That helps out a ton! Working on "shrinking" 20G for unbuntu now!

---

### Post by LewRockwell on 2010-04-26
make sure you have back-ups of everything you cannot afford to lose forever or spend time, effort, and money to recover.

we only installed Perfect Disk 11 to do these operations and several defrags and shrink sessions were required to beat down the NTFS Windows 7 partition.

we successfully shrank the NTFS Windows 7 partition down to 20GB(20,480MB).

we then uninstalled Perfect Disk and went back to our usual third-party defragger - Smart Defrag, which you can find easily along with most any other software at download.cnet.com

we also use BlackViper.com to get rid of Windows 7 bloat.

and don't forget to enjoy distrowatch.org as well!

.

---

### Post by joenewtzie on 2010-04-26
> **LewRockwell said:**
> make sure you have back-ups of everything you cannot afford to lose forever or spend time, effort, and money to recover.

we only installed Perfect Disk 11 to do these operations and several defrags and shrink sessions were required to beat down the NTFS Windows 7 partition.

we successfully shrank the NTFS Windows 7 partition down to 20GB(20,480MB).

we then uninstalled Perfect Disk and went back to our usual third-party defragger - Smart Defrag, which you can find easily along with most any other software at download.cnet.com

we also use BlackViper.com to get rid of Windows 7 bloat.

and don't forget to enjoy distrowatch.org as well!

.

Would you use more than 20G or keep it just at 20G? I could spare some more!

---

### Post by LewRockwell on 2010-04-26
also we wanted to comment regarding this from our earlier link post:

Quoting from:
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)> Also, shrinking the Win7 partition under Win7's Disk Management usually creates small Unallocated partitions (about 1 MB) both before and after the Win7 drive. If you resize with third-party partitioning utilities, these will not be created, or may even be removed, preventing Windows from booting.

after shrinking the NTFS partition down to 20GB we used gparted on the Puppy Linux 4.3.1 LiveCD to turn all that unallocated space into an ext2 partition as an experiment.

gparted did, in fact, leave some space after the NTFS partition as the above quote suggests is necessary.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

[http://www.puppylinux.com/](http://www.puppylinux.com/)

also we're using and promoting TinyCore quite a bit these days

[http://tinycorelinux.com/](http://tinycorelinux.com/)

.

---

### Post by joenewtzie on 2010-04-26
Well, here is my problem, it is only allowing me to shrink a total of 6187 Mb. Do I have to do the defrags again to increase that number to 20G (20480 mb)

---

### Post by LewRockwell on 2010-04-26
> **joenewtzie said:**
> Would you use more than 20G or keep it just at 20G? I could spare some more!

you can start with 20GB and then later on just clone it to another drive and then you can do more defrag and shrinkage as you desire

we smash our NTFS partitions down to an extremely small size so that they are as small as possible to facilitate very easy cloning via Clonezilla

[http://www.clonezilla.org/](http://www.clonezilla.org/)

you can see previous examples of our partitioning from this earlier thread:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by LewRockwell on 2010-04-26
> **joenewtzie said:**
> Well, here is my problem, it is only allowing me to shrink a total of 6187 Mb. Do I have to do the defrags again to increase that number to 20G (20480 mb)

as per the link we provided earlier:

[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

Perfect Disk 11 and Smart Defrag will both show you how the data is arranged on the current partition

it is up to you to decide how to proceed

we are only here to tighten up your learning curve a bit

at first it will feel like a wicked roller coaster

over time those knots in your gut will subside

.

---

### Post by joenewtzie on 2010-04-26
Ok, I ran the defrag with SmartDefrag, and then I used Ccleaner, rescanned the drives and still can only shrink 6187 mb

---

### Post by joenewtzie on 2010-04-26
ok, now I am doing some more of those setting adjustments on that previous link. Removing the back up and etc.  This should help!

---

### Post by LewRockwell on 2010-04-26
> **joenewtzie said:**
> ok, now I am doing some more of those setting adjustments on that previous link. Removing the back up and etc.  This should help!

smart defrag will not move Windows 7 immovables...

you must follow the directions from our privious link:

[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

you MUST use Perfect Disk 11 to defrag AND move the immovables

you cannot stand atop the mountian if you only climb halfway

.

---

### Post by joenewtzie on 2010-04-26
ok, I am downloading the free trial now and I will follow all the steps after a back up

---

