---
title: "Installation: Can't resize Windows partition"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by veroslav on 2010-08-20
Hi all,

I am trying to install Ubuntu 10.04 and keep my Windows XP installation (dual-boot).
I inserted the Live CD and followed the instructions until the "Partition Editor" step.
It displays my hard drive partitioned in three partitions:

1. Windows XP  (103 GB)
2. Recovery partition (7 GB)
3. Windows (internal something, not sure what this is for) (1 GB)

Now, according to the instructions on help.ubuntu.com, I should be able to right-click on my Windows XP partition and select "Resize". I can't see that option, but only "Change", "Revert", and one more option which I can't remember. Also, I can't see any sliders that are mentioned in the guide.

The strange thing is that if I choose "Change" for the recovery partition (2), it opens a new window giving me the option to resize the partition! But not for any other partition (1 or 3, well the same window opens but there is no resize option).

If it makes any difference, I can see that partitions 1 and 3 are NTFS while partition 2 is FAT32. Is this the cause of the problem? Also, I would like to get rid of the partition 2
completely, as I already burned it to the disk and would like to have more space for Ubuntu installation. How can I achieve this?

So the problem is basically that I can't shrink the Windows XP partition.

Any advice will be appreciated.

Kind Regards,
Veroslav

---

### Post by Rubi1200 on 2010-08-20
Try going to System > Administration > GParted (on the live cd) and then right-click on the XP partition and see if you can resize it. Theoretically, there should not be a problem with doing this.

Then, if successful run the installer on the desktop.

Hope this helps.

Report back if there are still issues.

EDIT:
you may need to defragment the XP partition from within Windows first before trying the steps mentioned above. And, possibly, run a chkdsk too.

---

### Post by TheCraneMan on 2010-08-20
> **Rubi1200 said:**
> Try going to System > Administration > GParted (on the live cd) and then right-click on the XP partition and see if you can resize it. Theoretically, there should not be a problem with doing this.

Then, if successful run the installer on the desktop.

Hope this helps.

Report back if there are still issues.

EDIT:
you may need to defragment the XP partition from within Windows first before trying the steps mentioned above. And, possibly, run a chkdsk too.

Yeah, defragmenting should help especially if you haven't done it in a while. I don't know about XP but I'm dual booting with Windows 7 and I resized my Windows 7 partition from within Windows 7 with the disk tool. You should try to resize it from within Windows XP first if GParted is having problems but if the above method works fine go with that too. XP should de-allocate the space if I remember correctly.

---

### Post by zeroseven0183 on 2010-08-20
I had troubles resizing my disk partition only to know that Windows had problems and requires some check disk to correct the errors.

---

### Post by Mark Phelps on 2010-08-22
I would rethink getting rid of the 7GB partition.  XP came on a CD, so there's no way an XP recovery image would take anything near that amount of space.  Even with a load of OEM junk, you're still talking a lot less than 7GB of space.

Maybe the OEM just created a large partition that is mostly empty. But, you should look inside that partition and see what is there before you remove it.

---

### Post by cool Cpu on 2010-08-22
[QUOTE=veroslav;9744635]Hi all,


i have win7 and had the same issue what i did was under win 7 i shrank volume c: 

made a new partition 40gb

than i booted up live usb and installed ubuntu on that partition without problem

ubuntu lucid has some fault cuz even when u shut down win 7 properly u still cant resize partition under ubuntu live usb

---

