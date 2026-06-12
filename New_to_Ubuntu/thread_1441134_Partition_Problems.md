---
title: "Partition Problems"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by clive littlewood on 2010-03-28
Hi All

I have a Toshiba NB200 netbook that I use for travel with a dual boot windoze 7 and Karmic UNR

Having used Lucid Beta now and loving it on my main comp I decided to upgrade the netbook Ubuntu partition to Lucid.

This went well right until the restart at the end, It would not boot.

Having tryed to solve this to no avail I decided to delete the Karmic partion and then do a clean install of Lucid.

The problem is when I fire up the live USB of Lucid and try to either format,delete or resize any of the Linux partions using gparted all the options are greyed out.

Any help to acomplish this from windoze or live USB would be gratefully received.

I have tried also to re install from the live USB but get the same problem,the partitions are in a mess !!!!!!!

Clive

---

### Post by readycarpenter on 2010-03-28
when booting from the usb drive, did you mount the drive you are trying to format?
if so gparted cannot format a partition that is mounted
hope this helps cheers

---

### Post by egalvan on 2010-03-28
Two things come to mind...

Highly likely that Linux installed on an extended partition

Highly likely that Linux created a swap partition


if these are true, then swap is automatically detected and mounted, which will make the extended mounted.
This will prevent any other partitions from being changed in any form, as readycarpenter pointed out.

Make sure any and all Linux partitions *inside* the extended are un-mounted, then un-mount the extended itself.

If the partitions are NOT logical (inside an extended) then you can simply un-mount them.

---

### Post by clive littlewood on 2010-03-28
Hi Guys

I will give this a try and report back

Thanks

Clive

---

### Post by clive littlewood on 2010-03-28
Hi

When I click on any of the Linux I get the "No Entry" sign and cannot access to delete or format !!!

Clive

---

### Post by Paqman on 2010-03-28
Right click on the swap partition and "swapoff". That should unlock all the other partitions inside your extended partition.

---

### Post by clive littlewood on 2010-03-28
Hi

Thanks paqman that did the trick   :D

Clive

---

