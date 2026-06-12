---
title: "How do You choose the right SSD drive ? ? ? ? ?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by suomalainen on 2011-02-19
Ubunteros,

I would like to learn more about SSD drives. Specifically, those drives that work with Ubuntu versions 10.04 and all future versions of Ubuntu yet to be released.

During my search, I've realised that some manufactures push the fact that their drives are designed for Windows 7 and the standards it supports. Trim support being one example. Below are 3 examples from vendors I found. Crucial doesn't seem to make any claim as to what o/s it prefers.

Be it as it may, what do I need to pay attention to when considering a SSD drive on which I will install Ubuntu?

Thank you,

Suomalainen


Corsair
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820233125](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233125)

TRIM Support The Corsair Force Series SSD’s offer TRIM support than can be enabled in Windows 7. Designed to maintain the performance of SSD at an optimal level over the lifetime of the drive, TRIM functions by actively deleting invalid data from the SSD’s memory cells to ensure that write operations perform at full speed. Since a memory block must be erased before it can be re-programmed, TRIM improves performance by pro-actively erasing pages containing invalid data, allowing the SSD to write new data without first having to perform a time-consuming erase command. To learn how to enable TRIM support in Windows 7, visit: [http://blog.corsair.com/?p=3468](http://blog.corsair.com/?p=3468).


Intel
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820167026](http://www.newegg.com/Product/Product.aspx?Item=N82E16820167026)

Intel SSD Toolbox with Intel SSD Optimizer The Intel SSD Toolbox with Intel SSD Optimizer provides a set of applications to easily manage the health and optimize the performance of your Intel SSD. The Intel SSD Toolbox includes a powerful set of management, information, and diagnostic tools, and is designed to work best with 34nm Intel SSDs. The Intel SSD Optimizer utilizes the new ATA Data Set Management Command (Trim Attribute) to help maintain your SSDs performance at "fresh-out-of-the-box" levels, and is specifically designed to run with Microsoft Windows 7. The Intel SSD Optimizer also works with Microsoft Windows Vista and XP operating systems as well.


Crucial
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820148357](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148357)

Push your performance The improvement in boot time and application load times push performance to new levels at the desktop too. You will experience improvement across a variety of common tasks such as viewing and editing photos, video, music and other media, gaming, communications, productivity and security.

---

### Post by HermanAB on 2011-02-19
So why would they *not* work with Linux?

---

### Post by walt.smith1960 on 2011-02-19
> **HermanAB said:**
> So why would they *not* work with Linux?

I think they'd work but I don't know if Ubuntu/Linux support the TRIM command.  From Wikipedia:

In [computing]("http://en.wikipedia.org/wiki/Computing"), a **TRIM** command allows an [operating system]("http://en.wikipedia.org/wiki/Operating_system") to inform a [solid-state drive]("http://en.wikipedia.org/wiki/Solid-state_drive")  (SSD) which blocks of data are no longer considered in use and can be  wiped internally. Note that despite the fact that TRIM is frequently  spelled in capital letters, it is not an acronym. It is merely a command  name. ...........................

 
[http://en.wikipedia.org/wiki/TRIM](http://en.wikipedia.org/wiki/TRIM)

---

### Post by kellemes on 2011-02-19
> **walt.smith1960 said:**
>  
[http://en.wikipedia.org/wiki/TRIM](http://en.wikipedia.org/wiki/TRIM)

It states it's supported since kernel 2.6.33.

I have no experience (yet) with SSD though..

---

### Post by HermanAB on 2011-02-19
Howdy,

I don't think that you need to worry about it.  We have been using SSDs for years in commercial and military applications.  SSDs have been common since the old Eee PC 701 was launched way back yoinks.

---

### Post by fabricator4 on 2011-02-19
You may be over thinking this.  It's just another storage device, basically.

One feature that I'd like to have on an SSD but don't have on the SSD in this 900SD is SMART.  I believe at least some, if not all new SSDs have SMART, check it out.

Beyond that, your decisions should probably be based on price/performance issues, not marketing blurb aimed users of that other OS.

Chris

---

### Post by suomalainen on 2011-02-20
I'm concerned about purchasing an SSD drive and having on it technical features that I cannot take advantage of. TRIM being one example although it was pointed out above that it is available? But does that mean it needs to be "turned on" or it's immediately available?

Does the Intel SSD Toolbox with Intel SSD Optimizer need to reside within a WINDOWS environment or is it totally Independence of o/s and operate on it's own? Just thinking that it may use windows to report information and data. If so, does Ubuntu have a comparable interlink?

Thanks

---

### Post by wizard10000 on 2011-02-20
> **suomalainen said:**
> I'm concerned about purchasing an SSD drive and having on it technical features that I cannot take advantage of. TRIM being one example although it was pointed out above that it is available? But does that mean it needs to be "turned on" or it's immediately available?

Does the Intel SSD Toolbox with Intel SSD Optimizer need to reside within a WINDOWS environment or is it totally Independence of o/s and operate on it's own? Just thinking that it may use windows to report information and data. If so, does Ubuntu have a comparable interlink?

I've been running 64-bit Kubuntu on a Corsair Extreme X64 for quite some time and have a few observations.  Just my opinions, please take what you like and leave the rest  ;)

As was already mentioned TRIM is supported at the kernel level - if the SSD has TRIM support all you should have to do is add a 'discard' switch to /etc/fstab.  TRIM support first showed up in 2.6.28 and full support (whatever that is) is in 2.6.33 and later.  Intel's tools are Windows tools and considering an SSD's performance is not reduced by fragmentation because there's no physical read/write head there's really no reason to run them.

There are some things you can do to improve performance and longevity, though - these are things that I did and you can try any or all if you like.

First, if there's a mechanical drive in the system don't put a swap partition on an SSD.  I use the SSD for / and a mechanical drive for swap and /home.

Second, unless you have a requirement for a last access timestamp on all the files on your SSD I suggest putting a 'noatime' switch on the SSD's entry in /etc/fstab.  This will eliminate a whole bunch of writes to the SSD.  I also do this for mechanical drives.

Stuff I haven't tried but might be useful -

Although you could create separate partitions on a mechanical drive for them I'd give some thought to booting from a Live CD and moving /var (or maybe just /var/log) and /tmp to a mechanical drive and just creating symlinks to them on the SSD.  The reason I'd use symlinks instead of actual partitions is that I prefer not to have 14 partitions on a drive  ;)

Some people say for maximum performance it's good to align partitions to erase block size but I personally think this is a little too much work for limited benefit, as on any given disk write you're talking about erasing only one more block than you would have if the partition wasn't aligned to erase block size.  On a really small file the worst case is you'd erase two blocks instead of one, and on a large file where you might ordnarily erase 500 blocks, if the partition's not aligned to erase block size at worst you'd erase 501 blocks instead of 500.

Anyway, I hope this helps.

cheers -

---

### Post by nrundy on 2011-03-20
Hi Wizard 10000 :)

I want to get an SSD but I want to do full disk encyrption. the Intel SSD Toolbox says it will run with encryption but it says it requires Windows.

Will I have problems running an SSD with encryption without running the Intel SSD Toolbox? (assuming the toolbox won't run on Ubuntu)

can I do full disk encryption on SSD trouble-free?

---

### Post by stmiller on 2011-03-20
Yeah Linux has trim support. Use Ext4, add option 'discard' to fstab options for trim.

The charts on these pages tell what controller is used on what model SSD:

[http://pcper.com/ssd](http://pcper.com/ssd)

The sandforce or intel controllers are typically the best performers at the moment.

---

### Post by nrundy on 2011-03-21
Thank you. So TRIM is still able run even when the whole disk is encrypted? I've read conflicting reports on this. I was hoping to get first hand report from someone with experience running the drive.

---

### Post by wizard10000 on 2011-03-21
> **nrundy said:**
> Thank you. So TRIM is still able run even when the whole disk is encrypted? I've read conflicting reports on this. I was hoping to get first hand report from someone with experience running the drive.

TRIM doesn't know whether the data's encrypted or not.  It's all zeros and ones to the drive  ;)

---

### Post by nrundy on 2011-03-21
sweet!  Okay, so if I run the SSD on the 11.04 Ubuntu it will have TRIM support. Will this TRIM setup get auto-configured on install? Or do I still need to do the fstab thing that has been mentioned in this thread previously? Once TRIM is established, does it all happen automatically? Or do I need to do some kind of "maintenance task" kinda like with a HDD I had to periodically run defrag. Do I need to periodically run something for the SSD?

Thanks so much guys for helping teach me :)

---

### Post by wizard10000 on 2011-03-21
> **nrundy said:**
> sweet!  Okay, so if I run the SSD on the 11.04 Ubuntu it will have TRIM support. Will this TRIM setup get auto-configured on install? Or do I still need to do the fstab thing that has been mentioned in this thread previously? Once TRIM is established, does it all happen automatically? Or do I need to do some kind of "maintenance task" kinda like with a HDD I had to periodically run defrag. Do I need to periodically run something for the SSD?

Thanks so much guys for helping teach me :)

You still need to do the fstab thing but the rest of it happens automatically.  No need to run anything else.

cheers -

---

### Post by Paqman on 2011-03-21
> **wizard10000 said:**
> 
Second, unless you have a requirement for a last access timestamp on all the files on your SSD I suggest putting a 'noatime' switch on the SSD's entry in /etc/fstab.  This will eliminate a whole bunch of writes to the SSD.  I also do this for mechanical drives.


Using noatime can apparently create problems for some software, i'd suggest using "relatime" instead.

It's a good idea to use ramdisks for things like /tmp if you've got an SSD. No need to be writing any of that to disk. If you really have to have your swap on an SSD (eg: laptop) then you can wind your swappiness down to zero quite happily in my experience.

> **nrundy said:**
> Thank you. So TRIM is still able run even when the whole disk is encrypted?

I don't know about whole-disk encryption, but it doesn't work on my encrypted home partition.

---

### Post by wizard10000 on 2011-03-21
> **Paqman said:**
> Using noatime can apparently create problems for some software, i'd suggest using "relatime" instead.

It's a good idea to use ramdisks for things like /tmp if you've got an SSD. No need to be writing any of that to disk. If you really have to have your swap on an SSD (eg: laptop) then you can wind your swappiness down to zero quite happily in my experience.

Of course everyone's experience is different but I've never had problems using noatime on an SSD.  As a matter of fact I also use it on my netbook, which has a mechanical drive - but then I probably don't use the same software as you  ;)

Also, I've tried several times with Kubuntu 10.10 to move /tmp to a ramdisk and the thing just hangs on boot.  Here's what I've tried -

```
# move /tmp to ramdisk
none   /tmp  tmpfs   defaults,noatime,mode=1777   0   0
```

I boot into single-user mode and move /tmp to /tmp.old before making the fstab change and then reboot - and I have yet for the thing to work right.  If you've got an idea where I'm messing this up I'd appreciate the feedback  ;)

---

### Post by Paqman on 2011-03-21
Off the top of my head: try just:
```
none /tmp tmpfs defaults 0 0
```

There's actually already a ramdisk at /dev/shm, btw. I also chuck a few other things like /var/log into RAM as well.

---

### Post by wizard10000 on 2011-03-21
> **Paqman said:**
> Off the top of my head: try just:
```
none /tmp tmpfs defaults 0 0
```

Tried that first - it won't even come up in runlevel 1 and I've tried it on both 32- and 64-bit machines.  Strange.

---

### Post by wizard10000 on 2011-03-21
> **Paqman said:**
> ...There's actually already a ramdisk at /dev/shm, btw. I also chuck a few other things like /var/log into RAM as well.

Do you just symlink /tmp into /dev/shm?

I thought about doing the same with /var/log and just running an rsync job to write the logfiles to disk at shutdown.

---

### Post by nrundy on 2011-03-22
> **Paqman said:**
> 
I don't know about whole-disk encryption, but it doesn't work on my encrypted home partition.

I emailed Intel some time ago about encryption. I assumed they would never respond cause so much time passed. But I got an email from them today. They said encryption process has nothing to do with performance degradation over time. Degradation will only occur if OS does not support TRIM or if AHCI is not selected before installing the OS. I have no idea what AHCI is. But Ubuntu 11.04 will support TRIM so I'm good for full disk encryption I guess.

---

