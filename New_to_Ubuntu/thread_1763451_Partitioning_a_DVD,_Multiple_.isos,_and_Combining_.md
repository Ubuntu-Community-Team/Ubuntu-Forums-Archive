---
title: "Partitioning a DVD, Multiple .isos, and Combining .isos"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-05-20
Ok, I want to create a DVD with all four K/X/L/Ubuntu live CDs on it. I'm going to make one with the LTS versions and one with the latest.So first question, is it possible to partition a DVD? If so, how can I do it? Can I install each Live CD on a partition and give me a boot option (with GRUB 2 or other bootloader). Or, can I combine all of this into one .iso file and burn it to the DVD? That way I could distribute it and make it easer for other people to do the same. My goal here is to make it easier to show people Ubuntu. With all of the derivatives in one place, it would be pretty easy. I will probably eventually get a USB to do this, but I don't have spare one. The only one I have is being used for all my Wii hacks.

---

### Post by psusi on 2011-05-20
No, you can't partition a DVD.  You will need to just extract the files from each, put the boot files in different directories, and tweek the boot loader to choose which one to boot, then burn that.

---

### Post by dniMretsaM on 2011-05-20
Ok, I don't know how to do that though. Could I get some more specific instructions please?

---

### Post by oldfred on 2011-05-21
multicd.sh - combine Linux ISOS into one CD
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
CD/DVD multiboot
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 


It is easier with a USB flash drive.

I did it manually with grub2 install before I found about these scripts:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by dniMretsaM on 2011-05-21
Awesome thank you! I'll mark this thread as solved. If I have more questions, I'll just re-use this thread! Yeah, I really do need to get a USB for this.

---

