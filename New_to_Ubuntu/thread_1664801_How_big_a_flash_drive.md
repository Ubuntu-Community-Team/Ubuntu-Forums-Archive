---
title: "How big a flash drive?"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by jackleg2011 on 2011-01-11
Hello,
 
I may be getting a laptop from a cousin and I have the sinking feeling the laptop will not have a cd/dvd included. Where I am now, I have no access to a dvd burner. If I wanted to install Ubuntu from a flash drive, how much in GB do I need?

---

### Post by Megaptera on 2011-01-11
Looking here [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download) it looks like min 2GB

---

### Post by spydeyrch on 2011-01-11
Well really you only need a 2 GB flash drive at minimum to have a live usb ubuntu and from there be able to install. If you want to make a persistent live usb ubuntu, then at the most, you can only use 4 GB.

Hope that helps. :)

-Spydey

P.S. I have a 16 GB drive broken into 2 partitions: one 4GB & one 12GB. The 4GB is used as a persistent live ubuntu. The persistent file allows me to make changes to my live ubuntu (install programs, settings, etc) and keep them. Whereas just the normal live ubuntu clears out any and all changes at time of restart/shutdown.

The second partition of 12GB is formatted as a FAT32 FS. This allows me to use my persistent live ubuntu and save any files (docs, pics, vids, etc) to the second partition for use later. Then, if I am booted into my windows system, or using a friends computer, or just need access to those files, I can plug in the flash drive and get access to the files without the need of booting up my persistent live ubuntu.

Does all that make sense? :)

---

### Post by C.S.Cameron on 2011-01-11
A Live USB takes up 0.7GB with no persistence, a 1GB flash drive should work.

There is no upper limit to USB drive size for installing Ubuntu.

---

### Post by spydeyrch on 2011-01-11
> **C.S.Cameron said:**
> A Live USB takes up 0.7GB with no persistence, a 1GB flash drive should work.

There is no upper limit to USB drive size for installing Ubuntu.


Really? There is no upper limit? I could have sworn that there was.:confused:

There have been multiple times when I went to use an 8GB or even 16GB flash drive as a persistent ubuntu. The flash drive was only one partition and it took up the whole drive. When I went to use the built in start-up creator in ubuntu, it would only allow me to use a max of 3.3 GB for the persistence file. The ubuntu iso used .7GB and the persistence used 3.3GB, therefore a total of 4GB. I would try to use more than just 4GB total (more than 3.3GB for the persistent file) but it wasn't doable by using that program.

Do you, C.S.Cameron, know of a different way to do it so that the persistence file can be greater than 3.3GB? That would be AWESOME!!!

-Spydey

---

### Post by Megaptera on 2011-01-11
> **spydeyrch said:**
> Really? There is no upper limit? I could have sworn that there was.:confused:

a different way to do it so that the persistence file can be greater than 3.3GB? That would be AWESOME!!!

-Spydey

From here [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Quote ". Note that the maximum space that can be allocated for persistence is limited to 4GB (maximum file size on a FAT32 filesystem is 4GB). This limit can be overcome and is explained later on."

and I think this is the part?

Quote "To make the persistence larger (> 4GB), while still on your normal Ubuntu Installation, mount the pendrive if it is not mounted already. View the files in the FAT32 partition of the pendrive. You will now be able to see a file called casper-rw. It will be the same size as the value set on the slider. Delete this file. Open gparted :

gksudo gparted

select the live usb. There will be a single partition only. Resize it so that you can have two partitions. You only need the current partition to be as large as it is already. You can safely move the resizing slider all the way to the left until there is just enough breathing space between the slider and the end of the first partition (coloured block). Make the newly created free space an ext4 or ext3 or ext2 partition and label it "casper-rw" without the double quotes. Hit apply changes. So now you have two partitions, the fat32 partition and the ext4 partition called casper-rw. This partition can be of any size and will be responsible for saving your data between boots. You can now boot using the usb drive and any changes you make will remain. "

---

### Post by C.S.Cameron on 2011-01-11
> **spydeyrch said:**
> Really? There is no upper limit? I could have sworn that there was.:confused:

There have been multiple times when I went to use an 8GB or even 16GB flash drive as a persistent ubuntu. The flash drive was only one partition and it took up the whole drive. When I went to use the built in start-up creator in ubuntu, it would only allow me to use a max of 3.3 GB for the persistence file. The ubuntu iso used .7GB and the persistence used 3.3GB, therefore a total of 4GB. I would try to use more than just 4GB total (more than 3.3GB for the persistent file) but it wasn't doable by using that program.

Do you, C.S.Cameron, know of a different way to do it so that the persistence file can be greater than 3.3GB? That would be AWESOME!!!

-Spydey



Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start Startup Disk Creator.
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by KyleRickards on 2011-04-18
Hi

I currently have Ubuntu running persistently on an 8 gig USB drive, is it worth me using a 16 gig one instead and if so, how big should I make the persistence file or should I partition the stick as 2 x 8 gig?

Thanks 
Kyle

---

### Post by mörgæs on 2011-04-18
If the computer is old, it does not support booting from USB. Which kind of computer is it?

---

### Post by mikewhatever on 2011-04-18
It would be worth it, if you needed more space. Do you need more space?

---

### Post by KyleRickards on 2011-04-18
Good point, I don't need it as such - just planning for the future I guess!

---

