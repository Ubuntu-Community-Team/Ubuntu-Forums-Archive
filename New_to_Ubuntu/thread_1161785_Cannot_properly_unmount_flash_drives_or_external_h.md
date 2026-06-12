---
title: "Cannot properly unmount flash drives or external hard drives"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by linuxneeewb on 2009-05-17
Dear All:

I recently installed Ubuntu 9.04, but I am having problem with unmounting external hard drives and flash drives.
My problem is that I can right click in the Desktop on the icon for the external hard drive or flash drive and click Unmount Volume; the icon will disappear, but neither the external hard drives nor the flash drives will be properly unmounted.
I know this for many reasons. First, the external hard drives will not turn off properly continue to run, and the usb flash drives will not turn off, and will not turn off their LED light. 

If you go to Places on the Desktop you will be able to see the icon of the External Hard Drive or Flash drive showing it is still there even though I have told it to unmount by right clicking it on the Desktop. 

Also if you go to to the File Browser in Gnome, you will see the icon there again. If you try to right click and unmount it there, the icon will still be there, and then it will just automatically reload itself.

I have a 8 GB Emprex flash drive, a 32 GB Corsair flash drive, a 500 GB Buffalo external hard drive, and a 1 TB WD external hard drive. They all fail to unmount properly. I did not have this problem with Ubuntu 8.10, Ubuntu 8.04, Windows XP, or Windows Vista. Any and all help is appreciated with this problem

Thank You

:popcorn:

---

### Post by diablo75 on 2009-05-17
They are actually unmounting correctly, but if they're still physically connected to the PC their icons will continue to be available via nautilus in case you want to mount them again.  You are confusing the act of mounting a drive vs. mounting a partition on that drive.  If a partition is mounted, you'll see it appear on your desktop.  If you unmount/eject that partition, it should disappear from the desktop but the physical drive itself will remain in your Places menu until you physically pull it from the USB port.  What you see in the Places menu is a representation of the physical drive itself, and not necessarily a representation of the logical partitions on said device.

You mentioned that the lights on a drive you unmount stay on.  I would only assume that's because the port itself is designed to provide power to anything attached to it, but do nothing more unless instructed by the OS.  So when you unmount something, the partition housing the data is closed and the OS verifies that no applications are using (reading/writing) before it logically detaches that partition from the file system.

---

### Post by z1000000 on 2009-07-30
Hi, I've got the same sort of problem as above. Up until today everything has been fine, it gone a little funny now though. I've had trouble mounting USB sticks and an external HD. So reading other threads, I've put them on and XP machine, and run them on PCLinuxOS, Open Suse, and even my EEE, and they've all mounted and unmounted fine. But on Ubuntu, one does the "Cannot unmount volume" thing, while the others unmount as usual. Any ideas please, it's really annoying that it only seems to do it on Ubuntu.

---

### Post by daimaru on 2009-07-30
i had the same problem with external HDs since 7.04. the right click "umount" command never worked. you can eject the drives from terminal using 
```
sudo eject /media/disktounmount
```With my HDs only if I eject them from terminal do they actually power down. If i use umount command it says that it unmounts them, but my external (usb) harddrive does not spin down.
Of course since its a bother you can write a nautilus script that does this on right click.

---

### Post by kansasnoob on 2009-07-30
I have no problem with external drives after installing "pmount". It's in Synaptic. Brief description from Synaptic:

> pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.


Of course you can install either using Synaptic or from terminal:

```
sudo apt-get install pmount
```

You should restart to be certain hal recognizes the changes.

---

### Post by z1000000 on 2009-07-31
Thanks guys. The sudo eject command didn't work, but I've found 

sudo umount /dev/sdb1

works.


Pmount doesn't seem to do anything either.

It's a total pain as it seem random, some sticks unmount normally, 
others came up with the error message. Reading about this, I think they 
all unmount properly, just sometimes I get the error message. It's such a small
thing yet seems unfixable, and it didn't do it last week!

Oh well, thanks all the same.

---

