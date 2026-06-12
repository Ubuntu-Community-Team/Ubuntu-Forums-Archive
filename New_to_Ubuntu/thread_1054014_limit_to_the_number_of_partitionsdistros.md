---
title: "limit to the number of partitions/distros?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by An_Dynas on 2009-01-29
I currently have 3 distros and Win XP installed on my hard drive.  Is there a limit to the number of logical partitions/distros I can or should create/install?

I've heard tell of people of who put lots and lots on the same machine.  Do I need to do anything special?  Thanks.

---

### Post by mikechant on 2009-01-29
As you probably know, you can have up to four primary partitions, and one of them can be an extended partition containing multiple logical partitions.

I can't find the reference at present but I remember reading that although you could create up to 63 logical partitions, Linux only safely supports a maximum of 15 logical partitions.
So assuming Windows is using 3 primary partitions (it often has boot and recovery partitions as well as the OS), and assuming you use the same swap for each Linux install and have a single shared /home partition, that would give you 13 partitions left = 13 distros/versions max.
 
If you really want more you could install a second hard drive or use USB sticks.

However, you might be better off looking at virtualization for experimental installs - you could have as many VM images with different distros etc. as you want, and when you've finished you can just delete the VM image file in a couple of seconds. Or you could have loads of VM image files stored on DVD or an external backup drive.

---

### Post by snowpine on 2009-01-29
I have experienced some strange boot problems when my partition numbers got into the double digits (/dev/sda10, /dev/sda11, etc) but I never looked into it too deeply. I agree that virtual machines are the way to go if you want to try lots of distros. Pick your favorite (fastest, most stable, whatever) as the host, then virtualize everything else. :)

---

### Post by mrbiggbrain on 2009-01-29
> **snowpine said:**
> I have experienced some strange boot problems when my partition numbers got into the double digits (/dev/sda10, /dev/sda11, etc) but I never looked into it too deeply. I agree that virtual machines are the way to go if you want to try lots of distros. Pick your favorite (fastest, most stable, whatever) as the host, then virtualize everything else. :)

agreed, but virtulization does require running an OS on top of an OS, and does limit some of the features that you can use.

---

### Post by -kg- on 2009-01-29
> **mikechant said:**
> As you probably know, you can have up to four primary partitions, and one of them can be an extended partition containing multiple logical partitions.

I can't find the reference at present but I remember reading that although you could create up to 63 logical partitions, Linux only safely supports a maximum of 15 logical partitions.
So assuming Windows is using 3 primary partitions (it often has boot and recovery partitions as well as the OS), and assuming you use the same swap for each Linux install and have a single shared /home partition, that would give you 13 partitions left = 13 distros/versions max.
 
If you really want more you could install a second hard drive or use USB sticks.

However, you might be better off looking at virtualization for experimental installs - you could have as many VM images with different distros etc. as you want, and when you've finished you can just delete the VM image file in a couple of seconds. Or you could have loads of VM image files stored on DVD or an external backup drive.

From [this page:]("http://tldp.org/HOWTO/html_single/Partition/")

> 3.4. Logical Partitions

One primary partition of a hard drive may be subpartitioned. These are logical partitions. This effectively allows us to skirt the historical four partition limitation.

The primary partition used to house the logical partitions is called an extended partition and it has its own file system type (0x05). Unlike primary partitions, logical partitions must be contiguous. Each logical partition contains a pointer to the next logical partition, which implies that the number of logical partitions is unlimited. However, linux imposes limits on the total number of any type of partition on a drive, so this effectively limits the number of logical partitions. This is at most **_15 partitions total on an SCSI disk and 63 total on an IDE disk._** 

I think there is a practical limit on the IDE disks, as well, *but* you should be able to extend this limit by using another physical hard drive.

> So assuming Windows is using 3 primary partitions (it often has boot and recovery partitions as well as the OS),

Eh?  Possibly the recovery partition, if you're using an OEM machine that the manufacturer didn't supply a disk with, but other than that, only one other partition.  Frankly, you can do away with the recovery partition as long as you get an installation/recovery disk to replace it.  Most manufacturers will supply one, if you ask.  But that's small change and not worth quibbling over...

Frankly, if I were to want to experiment with that many distros at a time (and if I had a computer that would boot from an external device), I think I would get an external hard drive to mount them on, preferrably hooked to an eSATA port, but firewire and even USB would work.  You can even get mobos now with external full-SATA connectors, to which you can put an internal SATA drive in an external housing and just connect them up directly to a SATA connector.

Or, as mikechant said, use them in VM for experimentation.  They may run a bit slower, but if you find one you would like to keep, then load that along with your other favs.  The others could be gone in a second, or you could store them externally for further experimentation.

Of course, if you're just doing it to see how far you can go with it (and I'm kinda with that idea myself...I always like pushing limits to see what I can get away with ;) ) then see how far you can go before it get's cumbersome.  I've seen a few sites that had experiments with mega-multi-boot setups.  Kinda sounds like fun.

---

### Post by unutbu on 2009-01-29
I chuckle every time I look at this:
[A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris]("http://www.justlinux.com/forum/showthread.php?t=143973")

It looks like a pretty good guide with lots of example GRUB entries.

---

### Post by An_Dynas on 2009-01-29
thanks all.

---

### Post by mikechant on 2009-01-30
RE -kg- 's quote
*This is at most 15 partitions total on an SCSI disk and 63 total on an IDE disk. *

I understood that when Linux changed (a couple of years ago) from using disk devices '/dev/fda' etc. to '/dev/sda' etc. for IDE disks, this was because it was now treating IDE discs as emulated SCSI disks, and that this was why the limit of 15 partitions would apply now to all SCSI **and** IDE disks under (current versions of) Linux.

But I could be wrong...


Also, I mentioned the possibility of 3 windows partitions because my Dell 530 desktop (possibly one of the most common PC models about), **does** have 3 windows partitions - a very small boot partition, a recovery partition and the main windows partition. Of course I could get rid of the recovery partition; I'm not sure how to get rid of the boot partition (I expect it would be easy to install without it if you had a proper windows install disc). I understand the point of a boot partition is to allow you to put the main windows partition in the extended partition if you want, but as Dell doesn't do this I'm not sure why boot is seperate.
Anyhow, some people don't like to mess with the windows partitions too much and may want to leave the 3 partitions alone if they have them, apart from shrinking the main windows partition to make space.

---

### Post by -kg- on 2009-02-01
> Also, I mentioned the possibility of 3 windows partitions because my Dell 530 desktop (possibly one of the most common PC models about), does have 3 windows partitions - a very small boot partition, a recovery partition and the main windows partition. Of course I could get rid of the recovery partition; I'm not sure how to get rid of the boot partition (I expect it would be easy to install without it if you had a proper windows install disc). I understand the point of a boot partition is to allow you to put the main windows partition in the extended partition if you want, but as Dell doesn't do this I'm not sure why boot is seperate.

I've never seen a set-up like that, but as I have custom built my last several desktops, I've never had an issue like that, and none of my laptops have ever come like that.

It might also be an added safety precaution, such as if a virus (or user ) FUBAR's the C: drive, you still have the boot sector intact and can easily access the recovery directory, but if that was the case, one would think that most all OEM computers would have it set up that way.

---

