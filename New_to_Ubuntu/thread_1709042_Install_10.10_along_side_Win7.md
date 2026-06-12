---
title: "Install 10.10 along side Win7"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by bob brazie on 2011-03-17
I am trying to install ubuntu 10.10 alongside of Windows 7.

During the install I do not get the option to "install alongside other operating system" the only choices are to "erase and use the entire disk" and "specify partitions manually"

I have shrunk the windows partition using the windows utility and have over 200gb of free unallocated space.

Please help if possible.

---

### Post by pricetech on 2011-03-17
Does windows show the free up space as allocated or unallocated ??

---

### Post by bob brazie on 2011-03-17
It shows as unallocated and is a black color where the others are blue and say primary.

---

### Post by _0R10N on 2011-03-17
When you reach the step in which you must select the type of partitioning to be used, select the option that says something like "select manually" (it should be one of the last ones). After that, the installer will check your disk and will display the partitions available in your partition table.

---

### Post by _0R10N on 2011-03-17
> **bob brazie said:**
> It shows as unallocated and is a black color where the others are blue and say primary.


Could you post a screenshot, please?

Thanks!

---

### Post by bob brazie on 2011-03-18
I pick a partition and it says I need to set a boot area and won't proceed.

---

### Post by oldfred on 2011-03-18
Have you already used all 4 primary partitions, so you cannot create more?

Post this from liveCD:

```
sudo fdisk -lu
```

---

### Post by Soulcage on 2011-03-18
Heres a guide with pictures [http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/]("http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/")

---

### Post by Mark Phelps on 2011-03-18
Fortunately, since you most probably already have four primary partitions, you can NOT follow the guide that was linked.  Had you done that, shrinking Win7 with GParted, you likely would have ended up with a corrupted Win7 install that would no longer boot.

Run the command that oldfred provided.  If you already have four primary partitions, you will have a lot of work ahead of you because you will have to remove an EXISTING partition to allow for the creation of a new one.

If you still then want to move forward with dual-booting, launch Win7, run the Backup feature, and create and burn a Win7 Repair CD.  You will need that later if problems occur with the Win7 boot loader from the dual-boot setup.

---

### Post by bob brazie on 2011-03-18
Thanks to every one. I did make windows un-bootable with everything I did so I just formatted and installed a clean Ubuntu 10.10. That was my ultimate goal anyway.

This is a new machine for my wife and she is a little afraid to go windowless even though our traveling laptop is only Ubuntu. She is a little familiar with it.

I have been Windowless since 08 and was pushing here away form it anyway. <g>

Thanks again to everyone. Bob.

---

