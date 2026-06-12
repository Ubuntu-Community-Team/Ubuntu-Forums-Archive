---
title: "use ubuntu to clone a windows hard drive with ntfs"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-03-13
tryed 
sudo ddrescue /dev/sda /home/custom/user/sda_image.img /home/custom/user/logfile

problem is would not mount under /mnt to see if it worked

so tryed

sudo ddrescue /dev/sda /home/custom/user/sda_image.iso /home/custom/user/logfile

the sda_image.img file is 55gb the other one tht is .iso is 0gb 

so now trying 

dd if=/dev/sda of=/home/custom/usr/sda_image.iso

waiting to see what is going on any body got any advice on how to make the image work?

---

### Post by howefield on 2011-03-13
I'd use clonezilla.

clonezilla.org

Not that DD won't work, just giving you an alternative option.

---

### Post by rosencrantz on 2011-03-13
dd_rhelp is faster that ddrescue, as it defers reading damaged sectors - for which ddrescue can take days... Simple dd will probably abort at the first error (I assume you are on a rescue mission?)
If it's an external drive, try plugging it into IDE/SATA, if you have a desktop computer, that might work even if USB mounting fails.
I logged some of my repair experiences here, [http://eumenidae.blogspot.com/2008/05/yet-another-crashed-hard-drive.html](http://eumenidae.blogspot.com/2008/05/yet-another-crashed-hard-drive.html), it's for FAT, but that shouldn't matter beyond mounting. 

Good luck,
rosencrantz

---

### Post by lance bermudez on 2011-03-13
where do i get dd_rhelp? I have
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
/etc/lsb-release (END) 

with gddrescue installed

---

### Post by rosencrantz on 2011-03-13
OK, I wasn't aware of the difference between dd_rescue (old) and ddrescue (new)... dd_rhelp improves on dd_rescue, but ddrescue seems to be better than both (see here: [http://www.toad.com/gnu/sysadmin/index.html#ddrescue](http://www.toad.com/gnu/sysadmin/index.html#ddrescue)) and you have the correct version already, so you needn't install anything new. Just don't waste your time with plain dd if you have a corrupted disk, try to get ddrescue to work.

---

### Post by rosencrantz on 2011-03-13
One more thing: The code you posted,
> **lance bermudez said:**
> tryed 
sudo ddrescue /dev/sda /home/custom/user/sda_image.img /home/custom/user/logfile
seems to be missing a partition identifier (like /dev/sda**5**), could that be your problem?

---

### Post by JKyleOKC on 2011-03-13
I did a Google search for ddrescue and came across some information that claims the "ddrescue" contained in the Ubuntu repositories is actually "dd_rescue" and that the real ddrescue has a different name: gddrescue.

It also appears, from the GNU ddrescue manual that I found through the search, that the program operates only on Linux file systems, not on NTFS -- although I could not locate this expressed explicitly anywhere, so my conclusion may not be accurate.

I have a damaged virtual hard drive (NTFS format) that apparently lost at least part if not all of its Master File Table but would like to recover as much data as possible from it. So far that has been none at all, but this thread offered the possibility of getting some new things to try. Does anyone know for sure if the new ddrescue is able to deal with NTFS devices, at either the whole-device or partition level? I can set up a /dev/loop device from the file, either way, but all attempts to actually mount it fail.

---

### Post by rosencrantz on 2011-03-13
ddrescue (as in gddrescue, you're right) shouldn't distinguish between file systems, as you don't mount anything - it just does a bit-by-bit copy of the partition and you can play around with the copied image without having to fear further data corruption/losses.
Still, you might not be able to mount your extracted image if the damage is severe. You can try searching for and extracting specific file types from the image with TestDisk. To attempt fixing the damaged file system, install ntfsprogs and use ntfsfix.

---

### Post by JKyleOKC on 2011-03-13
Many thanks! After ddrescue, testdisk found an NTFS partition in the image but said it could not recover it. I'll be trying ntfsfix next and won't continue hijacking this thread...

---

