---
title: "Windows and GRUB"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by PirateChef on 2009-02-19
I have two hard disks: one with Intepid on it, and the other just in ext3 format. I need to make some Shockwave files, but Linux doesn't have a good Flash toolkit. In order to avoid futzing around with Wine, I'm going to install Windows on the other drive, so that I can use Adobe Flash.

The question I have is: will the Windows installer overwrite my MBR, deleting GRUB, and keep me from accessing my Linux drive? Or, in other words: Do I have to install Windows first, and install Linux second?

---

### Post by mttman on 2009-02-19
do this :

```
Reinstalling Windows In A Dual Boot System

If you've ever setup a dual boot system with Windows and Linux before, you know that you have 
to install Windows first. Then you install Linux, which will include a boot loader that 
will allow you to boot into either operating system. But what do you do if want to 
reinstall Windows when you're using a boot loader like lilo or grub?

If you just put in the Windows CD and do a fresh Windows reinstall it will take over the 
system, and require you to reinstall Linux again, even if there's no need. What happens 
is Windows writes over the Master Boot Record (MBR), the first 512 bytes of the hard drive.
The MBR points to the partition to find the bootable operating system, and Windows points it to 
itself. To avoid this, you can save the MBR before you install Windows, and write it back after 
the install to resume using your dual boot system as usual.

I did this in Ubuntu, but it will work in any flavor of linux. On the command line, enter the following:

sudo dd if=/dev/hda of=/path/to/save/mbr.image count=1 bs=512

Substitute the path you want to save the MBR image and the correct device of your hard drive,
 which is probably hda. You've now saved a copy of your MBR from your dual boot system. At this 
point you should save MBR image to a USB drive or email it to yourself. Now go ahead and install Windows.

When the Windows installation is complete, you need to write back the original MBR. Boot into Linux with a 
knoppix disc and find your MRB image. From a terminal run the following:

dd if=/path/to/saved/mbr.image of=/dev/hda

Of course remember to sub in the path to your MBR image and the device name of your hard drive. That's it.
Reboot and things should be back to normal.
```

Now this is meant to be used in a dual boot system originally, so what you are going to need to do is 
basically follow these directions but edit your grub after in order to boot to windows, do you get it?

---

### Post by PirateChef on 2009-02-20
> **mttman said:**
> 
Now this is meant to be used in a dual boot system originally, so what you are going to need to do is 
basically follow these directions but edit your grub after in order to boot to windows, do you get it?

Yaarrghh...yes, I do. Maybe I should just try installing Flash into Wine, first.

---

### Post by caljohnsmith on 2009-02-20
Windows will overwrite Grub when you install Windows, but reinstalling Grub is usually really easy. You can reinstall Grub via these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by homey69 on 2009-02-20
easy yet semi-sloppy way of doing it as follows:

1. remove hd with ubuntu, dust off, put aside.

2. install windoze on other disk.

3. put back ubuntu disk, so _both disks should be in the case_.

4. install ubuntu (or any distro for that matter) on windoze disk, assuming you can spare 20gb or so, on it's own partition.

5. in the installation process the partition manager should see all OSes, therefore giving you three boot options when you power up.

---

