---
title: "How Can I Uninstall Ubuntu"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by fatgreta on 2009-08-29
Hi,

I have been messing around trying to get Ubuntu up and running, and have just tried reinstalling it to give myself a better sized partition. Something went wrong, I now seem to have two copies of Ubuntu on my hard drive and they both seem to have installed with some kind of error, probably due to having two different copies. Can anyone tell me how I can uninstall the, return my HD to its original state as a single OS (Win XP) system, so that I can start again clean? If need be, I can simply reformat my Hard Drive and reinstall windows, then reinstall ubuntu, but I'd love to avoid that part if possible. 

Thanks,

Chris

---

### Post by TeoBigusGeekus on 2009-08-29
Boot up with a winxp cd and enter recovery mode.
In the command line type
```
fixmbr
```
This will take care of grub.
In winxp, right click My Computer and select Manage.
Go to disk management, select the ubuntu partitions and format them.
The End...

---

### Post by fatgreta on 2009-08-29
> **TeoBigusGeekus said:**
> Boot up with a winxp cd and enter recovery mode.
In the command line type
```
fixmbr
```This will take care of grub.
In winxp, right click My Computer and select Manage.
Go to disk management, select the ubuntu partitions and format them.
The End...

Thanks for such a quick answer. I'm in the disk management part of my computer right now. When I right click on the ubuntu partitions, it gives me the option to "delete logical drive..." not format. Is that what I should do?

Thanks,

Chris

---

### Post by TeoBigusGeekus on 2009-08-29
Yes. Delete the partition and then format it.

---

### Post by fatgreta on 2009-08-29
> **TeoBigusGeekus said:**
> Yes. Delete the partition and then format it.

Thanks again. I've deleted all of the extra partitions. The disk manager now shows disk 0 as one partition, with 249GB capacity, 207 GB free space. The HD is 500GB, the 207 is what was freed up after deleting the logical drives that had ubuntu. When I right click on "Volume C:" I have the options to Open, Explore or change drive letters and paths. When I right click on the the free space indication, I have the options New Logical Drive or Delete Partition. The NLDrive takes me to the new partition wizard, the delete partition says "All data on this volume will be lost," which sounds scary. Do I use the new partition wizard?

Thanks again,

Chris

---

### Post by TeoBigusGeekus on 2009-08-29
Yes, as long as the wizard refers to the freed space only and not your win partition.

---

### Post by fatgreta on 2009-08-29
> **TeoBigusGeekus said:**
> Yes, as long as the wizard refers to the freed space only and not your win partition.

In the third step, it asks me how much space for the partition, and shows a maximum of 211GB. I think I may need to reinstall windows.

---

### Post by TeoBigusGeekus on 2009-08-29
No. Accept the max size and apply.

---

### Post by fatgreta on 2009-08-29
> **TeoBigusGeekus said:**
> No. Accept the max size and apply.

OK, then should I not apply a drive letter?

---

### Post by HermanAB on 2009-08-29
Howdy,

There are a thousand and one ways to zap a system, but all you really need to do is zap the Master Boot Record which is the first 512 bytes of a disk drive.

So if you write 512 zeroes to the disk, then any OS will install afresh again.  The easiest way to do that is to boot with a CD, e.g. Knoppix and do:
$ su
# dd if=/dev/zero of=/dev/sda bs=512 count=1

Et voila.

---

### Post by TeoBigusGeekus on 2009-08-29
Name the new partition D: or whatever you like.

---

### Post by fatgreta on 2009-08-29
> **HermanAB said:**
> Howdy,

There are a thousand and one ways to zap a system, but all you really need to do is zap the Master Boot Record which is the first 512 bytes of a disk drive.

So if you write 512 zeroes to the disk, then any OS will install afresh again.  The easiest way to do that is to boot with a CD, e.g. Knoppix and do:
$ su
# dd if=/dev/zero of=/dev/sda bs=512 count=1

Et voila.

Thanks for replying, but that's way too technical for me to even begin to understand.

---

### Post by fatgreta on 2009-08-29
> **TeoBigusGeekus said:**
> Name the new partition D: or whatever you like.
All right, it's formatting now. Thanks for the help so far.

Chris

---

