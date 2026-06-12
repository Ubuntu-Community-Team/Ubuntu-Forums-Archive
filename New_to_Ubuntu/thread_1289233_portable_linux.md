---
title: "portable linux"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by MelDJ on 2009-10-12
hi there, i am trying to install linux mint on my pendrive. i formatted it to fat32. i tried installing it with the portable linux app: [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)
but this error comes up: At least one sector from your USB drive is damaged.  Thus, Portable Linux cannot be installed in it.  Insert another USB drive and try again.

Details from the operating system:

badblocks: invalid option -- e
Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
 [-c blocks_at_once] [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
 device [last_block [start_block]]

any help?

---

### Post by theozzlives on 2009-10-12
Try unchecking the option to verify the drive and see what happens.

---

### Post by MelDJ on 2009-10-12
i have to add that i tried finding ways to solve this and other installation methods from google but have failed. any assistance is appreciated

---

### Post by MelDJ on 2009-10-12
> **theozzlives said:**
> Try unchecking the option to verify the drive and see what happens.

this comes up:
An unrecoverable error has stopped the creation of your Portable Linux drive.  Please report the details of this error to the Portable Linux developers, so we can fix it right away.

Details from the operating system:

mkfs.vfat: /dev/sdb1 contains a mounted file system.
mkfs.vfat 2.11 (12 Mar 2005)

does this mean i must delete the fat32 filesystem i made?

---

### Post by 45acp on 2009-10-12
I had the same error while using Portable Linux to make a bootable pen drive. Never did get it to work.

---

### Post by MelDJ on 2009-10-12
> **45acp said:**
> I had the same error while using Portable Linux to make a bootable pen drive. Never did get it to work.

hm..so is it a faulty pendrive, filesystem, or something else? i dont have other pendrives and this is quite new anyway

---

### Post by mcduck on 2009-10-12
How about trying with Ubuntu's own tool made for this purpose? You'll find it in System/Administration/USB Startup Disk Creator.

Alternatively Unetbootin is commonly used multi-platform tool for this purpose.

---

### Post by MelDJ on 2009-10-12
> **mcduck said:**
> How about trying with Ubuntu's own tool made for this purpose? You'll find it in System/Administration/USB Startup Disk Creator.

Alternatively Unetbootin is commonly used multi-platform tool for this purpose.

doesn't USB Startup Disk Creator install the ubuntu system on the computer to the usb?

---

### Post by MelDJ on 2009-10-12
anyway, i tried unetbootin and saw that only 6.9gbs of my pendrive is available. i tried to go to gparted to solve it, but it just greys out. then, i restarted the computer, and before ubuntu loads, an error comes up. it was around these lines, the partition table on device(my pendrive) is not recognizable. please run microsoft compatible fdisk to solve this. i booted into vista and went to computer managment and saw that my pendrive was partitioned into a 6.9gb partition and a 790mb one. i can format the 6.9gb one but not the 790mb one as an error comes up saying ' the operation is not supported with removable storage'.
i am really confused,,please help

---

### Post by mcduck on 2009-10-12
> **MelDJ said:**
> doesn't USB Startup Disk Creator install the ubuntu system on the computer to the usb?

No, it creates bootable USB installs from disk images and CD's.

Edit: what comes to the partition problem on the drive, my suggestion is to simply use gParted to remove all partitions from the drive and then create a new FAT partition in their place.

---

### Post by MelDJ on 2009-10-12
> **mcduck said:**
> No, it creates bootable USB installs from disk images and CD's.

thanks. i got it. mistook it for another program. now to my partition problem:)

---

### Post by MelDJ on 2009-10-12
i unmounted both volumes and then went to partition editor and was able to reformat it :popcorn:. installation in progress! thanks everybody. and thanks to mcduck for the program

---

### Post by MelDJ on 2009-10-14
actually it did not work. it just made a live linux mint while i want a persistent installed one. anyone?

---

### Post by mcduck on 2009-10-14
> **MelDJ said:**
> actually it did not work. it just made a live linux mint while i want a persistent installed one. anyone?

Then all you have to do is to use the normal installer, and point it to your pendrive when it asks where to install. And of course make sure it installs grub on the pendrive instead of your hard drive. You can do that by clicking on the Advanced.-button during the install.

Note that this kind of install will not work properly on all computers like the live install does, and also will decrease the lifetime of your flash drive significantly.

Personally, I use the live install and let the USB Startup Disk Creator use the available extra space on the drive to store my documents, updates and installed extra programs. Although booting the live system takes slightly longer, I can use the drive with *any* computer, and I'm still able to customize the desktop to my liking and install the programs I need.

---

### Post by MelDJ on 2009-10-14
> **mcduck said:**
> Then all you have to do is to use the normal installer, and point it to your pendrive when it asks where to install. And of course make sure it installs grub on the pendrive instead of your hard drive. You can do that by clicking on the Advanced.-button during the install.

Note that this kind of install will not work properly on all computers like the live install does, and also will decrease the lifetime of your flash drive significantly.

Personally, I use the live install and let the USB Startup Disk Creator use the available extra space on the drive to store my documents, updates and installed extra programs. Although booting the live system takes slightly longer, I can use the drive with *any* computer, and I'm still able to customize the desktop to my liking and install the programs I need.

do you mean that i should burn the .iso to a cd, boot into the live cd, then install mint to my pendrive there?

---

### Post by babloo75 on 2009-10-14
Just came across this website. Thought it will help someone
[http://www2.mandriva.com/flash/](http://www2.mandriva.com/flash/)

---

### Post by MelDJ on 2009-10-14
thank you babloo75 but i did not find anything helpful there__

---

### Post by mcduck on 2009-10-14
> **MelDJ said:**
> do you mean that i should burn the .iso to a cd, boot into the live cd, then install mint to my pendrive there?

Yes, or if you have another flash drive or memory card available you can use that instead of burning the .iso to a CD.

---

### Post by MelDJ on 2009-10-14
> **mcduck said:**
> Yes, or if you have another flash drive or memory card available you can use that instead of burning the .iso to a CD.

thank you very much for your help throughout my plight mcduck. my dad went to buy a cd rw. after trying i will report back here

---

### Post by babloo75 on 2009-10-14
Probably this will help:

[http://www.pendrivelinux.com/install-fedora-9-to-a-flash-drive-using-windows/](http://www.pendrivelinux.com/install-fedora-9-to-a-flash-drive-using-windows/)
[http://www.pendrivelinux.com/make-your-own-portable-mandriva-flash/](http://www.pendrivelinux.com/make-your-own-portable-mandriva-flash/)

[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)
[https://fedorahosted.org/liveusb-creator/wiki/Screenshots](https://fedorahosted.org/liveusb-creator/wiki/Screenshots)

and many more versions of portable Linux on drives

---

