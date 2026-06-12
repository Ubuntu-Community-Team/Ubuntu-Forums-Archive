---
title: "Easiest method to migrate from windows 7 to ubuntu...?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-19
What is the easiest way that I can make this switch? What I have to work with:


[LIST=1]
[*]1 230GB HDD, 1 partion so far making use of all available space. Windows 7 installed. About half of this diskspace is in use by win7/my files.
[/LIST]
What I would like:

[LIST=1]
[*]To be able to go back to windows 7 and my files stored there as opposed to make one big leap.
[*]I have a work environment set-up and I can't do a fast switch, this will take time
[*] I also need to be working as I don't have a lot of time to be able to contribute to migrating all in one day.
[*]I also like to use windows7, and I don't want to reconfigure all that stuff again! So I would like to still be able to continue to access that OS indefinitely.
[/LIST]

What are the best methods to accomplish this?

---

### Post by TurnOfTide on 2010-02-19
Not to answer my own question, but perhaps I could run a VM of Ubuntu, migrate from running the VM.... but if I do this, can I can make this OS (the one installed on a VM) as a bootable OS? Would there be anyway to get the files/settings from there, safely at that, to a bootable version? I think this would be a pretty nice solution for me.

---

### Post by wil08son on 2010-02-19
You could always dual boot, which would allow you to use Ubuntu and Windows 7.

---

### Post by bcbc on 2010-02-19
Use the Windows 7 disk management tools to shrink your existing partition and create a new extended partition, then install as dual boot.
Backup your data first.

Here's a [walkthrough]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") on shrinking your partition.

---

### Post by geoff07 on 2010-02-19
Whatever you do, I suggest you create a separate partition for all of your data. That way, if you need to reinstall windows or ubuntu you don't risk your data.  If you use ntfs as a format it can be read by both operating systems. Then you can just back up that drive in its entirety.

---

### Post by TurnOfTide on 2010-02-19
Good point.... do you use a seperate partition or drive for your data in your current setup?

---

### Post by lkraemer on 2010-02-23
Purchase a New drive and install Ubuntu!  DONE!

lk

---

### Post by Ozymandias_117 on 2010-02-23
@lkraemer Um... What does buying a new hard drive accomplish? lol

---

### Post by Mark Phelps on 2010-02-23
> **lkraemer said:**
>  ... 2.  Download Clonezilla, and use it to image your current drive to the new drive

This is needlessly asking for trouble ... 

In some cases, the SN of the drive where MS Windows was originally installed is part of the hash code sent to MS when the OS is activated.  Moving the OS to a different drive "breaks" that code and can deactivate the OS, forcing the OP to have to telephone MS Support to get a new product key.

If you've going to buy a new drive, just install Ubuntu on that drive and create a large data sharing partition on it as well.

That gives you the same results without the hassles of dealing with MS OS activation problems.

---

### Post by PhoHammer on 2010-02-23
> **bcbc said:**
> Use the Windows 7 disk management tools to shrink your existing partition and create a new extended partition, then install as dual boot.
Backup your data first.

Here's a [walkthrough]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") on shrinking your partition.

Did they fix the shrinkage tool in Win7? I know in Vista, the tool liked to say that Vista is using ~95% of the drive, even though it would be using <50%. And this is after defragmentation (which was horrible in Vista). At least Win7 has a better defragger, with a progress indicator.

Anyways, I vote for this method if you can get Win7 to shrink its own disk. Ubuntu will detect the Windows installation and add it to GRUB, letting you choose between the two when you boot. You can also switch back to Win7's bootloader I think, if that's what floats your boat.

Edit: but do ***defragment*** Windows 7 first! (it's in accessories>system tools, I believe)

Good luck!

---

