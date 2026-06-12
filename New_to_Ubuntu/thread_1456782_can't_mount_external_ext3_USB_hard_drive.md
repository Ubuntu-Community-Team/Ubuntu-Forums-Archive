---
title: "can't mount external ext3 USB hard drive"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by BROOKLYN-BEN on 2010-04-17
I'm a complete noob to Ubuntu.  I've just installed Ubuntu 9.10 as a virtual machine through VMware Fusion, hosted on my Macbook Pro (snow leopard).

I have an old 320G hard drive, formatted in ext3) in a powered external usb enclosure that has all of my music library on it.   I'm currently unable to mount this external drive to my Ubuntu installation. 

When I plug the drive into my USB  port, it does not appear on my desktop or in Disk Utility.

So far I've tried the following:
- I plugged a USB thumb drive into the same port I had plugged the ext drive into and it mounted automatically.
- I followed the steps in the Ubuntu manual for mounting a USB drive, configuring auto mounting, etc. ([https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)).   All my settings were already configured to allow automounting, so I tried to follow the steps for manual mounting and got stuck on the first step in which it instructs you to use "sudo fdisk -l" to find your device.   I've pasted my results below but which if any of these are my USB drive?

```
ben@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4b25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2496    20049088+  83  Linux
/dev/sda2            2497        2610      915705    5  Extended
/dev/sda5            2497        2610      915673+  82  Linux swap / Solaris
```


My linux skills are minimal at best, but I'm wondering if at some point in the past this USB drive was incorrectly Unmounted.   Would that explain the problem I'm having?   If so is there any hope for recovering my data?

Thanks, Ben

---

### Post by IndyGunFreak on 2010-04-17
That looks like your main drive, and it is in 3 different partitions.  If it was seeing a *separate* USB drive, it would be sdb, sdc, etc.  Plug your thumb drive in and run the command again, and you'll see.  As it is, it is showing sda(which I assume is your main drive) is split into 3 partitions.

Are you sure the USB cable is properly attached to the drive?  Drive is turned on?  

IGF

---

### Post by BROOKLYN-BEN on 2010-04-17
Thanks IGF, that's kind of what I suspected.

So now my question is why isn't my ext3 formatted USB drive appearing when I run sudo fdisk -l?

---

### Post by -humanaut- on 2010-04-17
Do you have a mount point for it in fstab? try looking in sudo nano /etc/fstab

---

### Post by BROOKLYN-BEN on 2010-04-17
Doesn't look like it:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3b6fad4f-d87a-4e32-a633-000d26be93e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63d1ba78-61a1-470b-9f30-45e6e7a997d2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by IndyGunFreak on 2010-04-17
I'm thinking a bad USB cable.

Or the enclosure its self is bad, and is not communicating w/ the drive.  How handy are you dealing w/ computer hardware?

---

### Post by -humanaut- on 2010-04-17
You could try creating a mount point for it

---

### Post by BROOKLYN-BEN on 2010-04-17
Ok, I don't really know what it means to mount a point, but I followed the instructions in the manual and got this:

```
ben@ubuntu:/media$ sudo mount -t ext3 /dev/sdb1 /media/external -o uid=100,utf8,dmask=027,fmask=137
mount: special device /dev/sdb1 does not exist
ben@ubuntu:/media$ 

```

---

### Post by VeeDubb on 2010-04-17
> **IndyGUnFreak said:**
> I'm thinking a bad USB cable.

Or the enclosure its self is bad, and is not communicating w/ the drive.  How handy are you dealing w/ computer hardware?

^This


I have an external USB hard drive and when I plug it in, it just get's auto mounted with a link right on my desktop in the exact same manner as when I plug in an SD card, USB thumb drive, or insert a CD/DVD.

It's my understanding that the same software handles all of the above, and does not require anything in terms of manual configuration.

That leaves 2 options.

A.  You have a hardware problem either with the USB port you're trying to plug it into, the USB cable you're using for the connection, with the enclosure that holds the drive, or the drive itself.

B. The software that handles automatically mounting external media is not working properly.

You can test both of those fairly quickly.  Let's start with Option B.  Put a CD in the drive.  Does it mount?  Plug in a USB thumb drive (but not into the same USB port you were connecting your external hard drive.  Does it mount?   If they both mount, it's not the software.  If one or both fails, you've got a problem.


Assuming the software that auto mounts external storage is working, you can easily test the hardware.  

1. Plug it into a different port.  Fixed?  The problem is a bad USB port on your computer.  Not fixed?  Move on.

2. Try a different USB cable.  Fixed?....

3. If neither of those worked, then the problem is either the enclosure, or the drive inside the enclosure.  but now we're into some serious hardware debugging issues, and possibly some advanced data recovery techniques if the data on that drive is important to you.

---

### Post by IndyGunFreak on 2010-04-17
He said his in the original post, his thumb drive plugged into the same port mounted automatically, so I'm fairly confident this is not a software issue.

Brookly-ben   Is this a PC or laptop?  Any chance you can pull the drive out of the enclosure, and mount it inside your case, so you can see if its the drive or the enclosure?  That's what I would do, but I don't know how familiar with hardware you are.

---

### Post by BROOKLYN-BEN on 2010-04-17
Yeah, it's looking like a hardware problem.  As I mentioned in my first post, I tried a usb thumb drive in the same port and it worked fine.

This is a laptop and the external drive in question is a 3.5, so unfortunately I can't pop it in the case as you suggested.

So with the deductions i've made with help from both of you, I think it's down to the USB cable, the enclosure, or the drive itself.   Unfortunately I don't have another cable that fits the enclosure so this will have to wait till I can get to an electronics store.

I'll post back here when I find out more. Thanks

---

### Post by MrWES on 2010-04-17
Unplug the drive and then plug it back in. Now open a terminal and type:

```
dmesg | tail -25
```

Look for any information concerning your drive or errors.

Bill

---

### Post by BROOKLYN-BEN on 2010-04-17
Bill,

I tried the dmesg command as you suggested.   Plugging in the usb hard drive has no effect on the output of this command.  In contrast, I tried plugging in a usb thumb drive to the same port and immediately got something regarding it in the dmesg output.    

I would like to think that if my external drive was corrupted I would at least be getting some kind of error message.   But the fact that I'm getting nothing gives me hope that perhaps the cable or usb enclosure are faulty.   At least I sure hope this is the case, as I have a lot of valuable data on that drive.

---

### Post by VeeDubb on 2010-04-18
The other thought that comes to mind, is you said it's a "powered" drive, which to me means that it has it's own external power supply.

With most of those drives, the drive will spin up as soon as you connect the power.

Is the drive spinning up at all?  Are there any indicator lights on the enclosure that 'should' light up, but aren't?  It may be something as simple as a bad power supply for the enclosure.

---

### Post by BROOKLYN-BEN on 2010-04-18
Yep, the drive has its own power supply.  The drive sounds like its spinning up fine and the indicator light is lighting up normally.

In the next few days I hope to try this drive out in another enclosure.

---

### Post by BROOKLYN-BEN on 2010-04-20
Ok, looks like it was just a bad USB cable.   I dug up another one that fit that drive, connected it to my laptop and the drive shows up fine.     I feel stupid for not trying that earlier.  

In any case, thanks everyone for taking the time to help me out!

---

