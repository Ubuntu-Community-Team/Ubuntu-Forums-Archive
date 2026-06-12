---
title: "Media Drive Not Ready???"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by Lvcoyote on 2010-12-12
I reworked my computer including a new case and water cooling stuff.  The motherboard, all hard drives and everything else is still the same.  Upon booting the system I am now getting the following error:

The media drive for /media/Local_Disk is not ready yet or not present.
Type S to skip or M for recovery.

Pressing S does nothing and the system just stays at that message screen, I can hit M and get to terminal.  I do remember when setting the system up a while ago I had it auto mount a spare hard drive that is full of different stuff/files.  I'm pretty sure its trying to mount that spare drive.  This makes no sense though as I wrote down and triple checked where each drive was attached to the motherboard before beginning the process.

The system is set up as follows:
Sata Drive X 2 for Windows 7 (Using Raid 0)
Sata Drive for Linux
Sata Drive for storage (Probably the media drive the boot process is complaining about)

I need to know if there is anything I can do after pressing "M for recovery" that will get me to the desktop?

---

### Post by sikander3786 on 2010-12-12
We need to see the output of these commands.

```
cat /etc/fstab
```

```
sudo blkid
```

I know you won't be able to copy/paste the text as your computer is not booting to the desktop. This is either a problem with a wrong entry, wrong mount path in fstab or the UUIDs are not matching between fstab and blkid output. See if you can figure it out yourself.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you need to edit /etc/fstab,

```
sudo nano /etc/fstab
```

Otherwise, we need to see the output or a screenshot...

---

### Post by Lvcoyote on 2010-12-12
Thanks for the help sikander, it got me pointed in the right direction and I'm able to boot back to the desktop now.

I ended up having to comment out two lines in fstab and ended up with the following:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#/dev/sdh1	/media/Local_Disk	ntfs-3g	defaults,locale=en_US.utf8	00
/dev/sda1	/	ext4	errors=remount-ro	0	1
#/dev/sdg5	none	swap	sw	0	0

```

I also remembered that I removed a 3.5 inch card reader from the system during this rebuild, is that the SDG5 drive?

If both items above that I commented out are un-commented then the system will not boot, if I comment out the sdh1 drive I still get the error message but booting continues after a few seconds.  Only commenting both entries out give me an error free boot.

Here is the output of blkid:
```

/dev/sda2: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc1: UUID="0b14fb15-2e67-4e85-939c-33246bc0f235" TYPE="ext4" 
/dev/sdc5: UUID="c45745e1-04e0-4dd3-af80-8271fed514b6" TYPE="swap" 
/dev/sdd1: LABEL="Local Disk" UUID="0E3A78113A77F455" TYPE="ntfs" 

```

Thanks again!

---

### Post by sikander3786 on 2010-12-13
sdh and sdg drives are not present?

Your output of blkid is not showing the UUID of sda1.

Originally, sdc5 is the swap partition while sdg5 was defined as swap in your fstab.

Try this command to find UUID of '/' partition.

```
sudo blkid -c /dev/null
```

And in /etc/fstab, instead of this line,

```
#/dev/sdg5    none    swap    sw    0    0
```

Your swap needs to be defined like this.

```
UUID=c45745e1-04e0-4dd3-af80-8271fed514b6  none  swap  sw  0  0
```

And once you find the blkid for your '/' partition, it should be defined like this.

```
UUID=xxxxx  /  ext4  relatime,errors=remount-ro  0  1
```

You seem to have Raid setup and I'm not sure how to work with that.

Better to define mounts using UUID instead of /dev as it saves you many troubles when you switch the drives master/slave or add new drives. Even if they get renamed e.g, from sda to sdb, Ubuntu would still be able to recognize them by their UUIDs.

---

### Post by coffeecat on 2010-12-13
I don't have that much to add to what sikander3786 has already said. I'd certainly agree about using UUIDs in /etc/fstab. Rather curiously, SATA devices (with some motherboards) can change from sda to sdb (for example) and back again. I've seen this. I wonder if the sda1 referenced as your root partition in your /etc/fstab is now the sdc1 partition showing up in blkid. Using the UUID would certainly get around that issue.

Just a couple of other comments.

There's a syntax error in the fstab line below. Although the non-existence of /dev/sdh1 would explain the S/M prompt, the syntax error may explain the peculiar behaviour thereafter. There should be a space between the two zeroes which are fields 5 and 6.

> **Lvcoyote said:**
> ```
#/dev/sdh1    /media/Local_Disk    ntfs-3g    defaults,locale=en_US.utf8    [COLOR=Red]00[/COLOR]
```

Also:

> **Lvcoyote said:**
> I also remembered that I removed a 3.5 inch card reader from the system during this rebuild, is that the SDG5 drive?

As sikander3786 has said, sdg1 refers to a swap partition yet your swap partition is sdc1. What experience I have of card readers is that they are detected by the kernel as sdx devices, usually one per slot. In my 2-harddrive machine with a 2-slot reader, the card reader is seen as sdc and sdd. You wouldn't have a fstab line for a card reader because a card is auto-detected and auto-mounted when inserted.

---

### Post by Lvcoyote on 2010-12-13
I appreciate the help guys, but the system is booting just fine now and everything works just as before.  I don't plan on adding any additional drives to the system as the motherboard ports are full.  I'll probably be upgrading to 11.04 when it comes out anyway, so for now I think I'll call it good enough for fear of hosing the system again.

---

