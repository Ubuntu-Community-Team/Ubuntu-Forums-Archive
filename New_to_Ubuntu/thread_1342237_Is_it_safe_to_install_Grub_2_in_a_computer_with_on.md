---
title: "Is it safe to install Grub 2 in a computer with only Win7 ?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by *g!t5^_)*(H on 2009-11-30
Hi,

I've a new computer, I bought it because I need windows from my university lessons (it's a pitty). I would like to install Ubuntu also and 'dual boot' to use windows when it's only mandatory.

But I'm afraid.

This computer has no CD, but the 'repair windows' software depends on it, so I've no way to restore windows if I break everything. 

The computer is a Sony Vaio W with Windows 7.

From your experience, is it safe for me to install Ubuntu ? Will Grub2 detect Windows7 in an appropiate manner ? Will I break Windows somehow because Grub2 sometimes fails ?

:s :s :s

Thanks in advance for your advice.

---

### Post by bodhi.zazen on 2009-11-30
In general you will be fine.

If you have problems, however, you should have a back up plan, ie back up or way of restoring Windows.

There are several applications which will image your HD, partimage is one of many ...

---

### Post by Mark Phelps on 2009-11-30
Every PC sold in the US from a reputable manufacture, which comes preloaded with Win7, MUST provide a way to restore the computer to its initial condition -- that's a requirement levied against OEMs by MS in order for them to do business.

That being the case, the OEM is free to choose HOW to provide that restoration capability.

Some provide a restore DVD that is completely self-contained; others provide a recovery CD that boots into a recovery environment and loads an image stored in a hidden partition; others provide a Function key that you press when starting your machine and it will then perform the restoration.

YOUR machine will come with one (or more) of these.

Contact Sony to find out which it is.

However ... what a restoration will do is completely wipe out all files, applications, and settings -- which is quite extreme if all you need to do is restore boot capability.

Win7 typically comes with a built-in function to create and burn a Recovery CD -- one that can be used to repair the installation, not to restore it.

Click the start button, enter "backup", select the option.  On the page you will see an entry for creating a system repair disk.

Grab yourself a blank CD, select that option, and burn the recovery CD.

That will allow you to restore boot capability if your dual-boot experiments corrupt it.

Also, do NOT allow the Ubuntu installer to shrink your Win7 partitions to make room for Ubuntu.  Use the Win7 Disk Management utility to shrink the partition instead.

---

### Post by anders_c_ on 2009-11-30
I think he means that his computer doesn't have a cd drive, not that he didn't get a recovery cd along with it. Sony Vaio W series is a netbook. So burning cds isn't an option unless he has another computer, or usb burner.
I have dual-booted for over 2 years and never had any trouble with ubuntu messing up my windows partition, but perhaps I'm just lucky...

---

### Post by sandyd on 2009-11-30
> **optimisme said:**
> Hi,

I've a new computer, I bought it because I need windows from my university lessons (it's a pitty). I would like to install Ubuntu also and 'dual boot' to use windows when it's only mandatory.

But I'm afraid.

This computer has no CD, but the 'repair windows' software depends on it, so I've no way to restore windows if I break everything. This is not a pitty, this is a f*** s*** (thanks M$)

The computer is a Sony Vaio W with Windows 7.

From your experience, is it safe for me to install Ubuntu ? Will Grub2 detect Windows7 in an appropiate manner ? Will I break Windows somehow because Grub2 sometimes fails ?

:s :s :s

Thanks in advance for your advice.
grub 2 WILL detect windows 7.
just out of curiousity, can you do a ```
sudo fdisk -l
```while running from livecd?
some computers (such as mine) have  a hidden restore partition that shows up only in grub2. it is hidden if your using the windows bootloader. if there is one, grub2 will automatically detect it and add an entry for it in the boot menu.

oh yeah, and remember to let WINDOWS do the partition shrinking or else it wont boot up after (Control Panel -> Administrative tools)(its somewhere is there.....)

---

### Post by *g!t5^_)*(H on 2009-11-30
Thank you very much to everyone. I was just worried, but I installed Ubuntu 9.10 normally and dual boot works perfectly with Windows 7.

I'm from Europe, and be sure there's no restore CD in the box. But well, Ubuntu is working wrigt, I'll use windows just for my university lessons, and I'll remove it next summer (yes I know I paid a lot of money for it, but have you played with Win7, it's horrible!).

Thanks again :D

---

### Post by Geoff918 on 2009-11-30
> **optimisme said:**
> Thank you very much to everyone. I was just worried, but I installed Ubuntu 9.10 normally and dual boot works perfectly with Windows 7.

I'm from Europe, and be sure there's no restore CD in the box. But well, Ubuntu is working wrigt, I'll use windows just for my university lessons, and I'll remove it next summer (yes I know I paid a lot of money for it, but have you played with Win7, it's horrible!).

Thanks again :D

Ah, it was clear enough you weren't from the US. You called it "University Lessons". If this post wasn't so far down I would have pointed out that likely incorrect assumption to one of the original replies.

As a general note: anything to do with Ubuntu and very core items is tested and not too experimental by the time of adoption. I actually think GRUB2 is older than Ubuntu. But, nobody that wants to be taken seriously uses new technology at its roots. Far too dangerous. What would you think if you were using your Windows computer and randomly the system deleted its boot up or broke its file system in the midst of normal usage? Nobody would run such a system, and it would be mocked. So, GRUB2 is new to Ubuntu but rest assured, it's not new.

:P

---

### Post by nazgulord on 2009-11-30
> **Mark Phelps said:**
> 
Also, do NOT allow the Ubuntu installer to shrink your Win7 partitions to make room for Ubuntu.  Use the Win7 Disk Management utility to shrink the partition instead.

This intrigues me, as I was also planning to run Win 7 dual boot with Ubuntu. Why exactly is it that Ubuntu's partitioning messes up Win7?

Thanks,

nazgulord.

---

### Post by Geoff918 on 2009-11-30
> **nazgulord said:**
> This intrigues me, as I was also planning to run Win 7 dual boot with Ubuntu. Why exactly is it that Ubuntu's partitioning messes up Win7?

Thanks,

nazgulord.

I'm not sure, but I would be surprised it the issue is not more with Win7 than Ubuntu. More than likely Win7 has "control issues" and will believe itself to be corrupted if it doesn't move the "drive" boundaries. Also, I'm sure it's a safer operation because Win7 would move any critical files or any swap space it deems necessary itself rather than being imposed upon.

---

### Post by sandyd on 2009-12-01
> **nazgulord said:**
> This intrigues me, as I was also planning to run Win 7 dual boot with Ubuntu. Why exactly is it that Ubuntu's partitioning messes up Win7?

Thanks,

nazgulord.
windows 7 has a "partition size" check each time it boots up.

---

### Post by Mark Phelps on 2009-12-02
> **nazgulord said:**
> This intrigues me, as I was also planning to run Win 7 dual boot with Ubuntu. Why exactly is it that Ubuntu's partitioning messes up Win7?

I don't think anyone knows exactly ... It's just that a LOT of folks reported inability to boot into Vista after using Ubuntu installer to "shrink" their Vista OS partition to make room for Ubuntu.

Initially, it was though that moving the start of the Vista OS partition caused this problem because folks were checking a box to allow that to happen, but later, folks reported the same problem when all they were doing was choosing side-by-side installation and not manually messing with the partitions.

The problem was easily (but not quickly) fixed by booting from a Vista installation DVD and running Startup Repair several times -- but since most people who bought machines preloaded with Vista had NO such DVD, and no way to make one, that left people in the position of having unbootable Vista installations.

Win7 uses the same filesystem as Vista, except, it now complicates matters by inserting its own "boot" partition into newly formatted volumes.

It also provides the ability to create and burn your own Win7 Recovery CD you can use to repair the boot loader.

So, the problem isn't as bad in Win7, but the cautions still remain to prevent folks from corrupting their MS Windows installation.

---

