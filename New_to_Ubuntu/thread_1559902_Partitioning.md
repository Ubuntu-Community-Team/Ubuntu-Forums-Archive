---
title: "Partitioning"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by eithantlv on 2010-08-24
Hello,
If I have 130GB free space on Hard Drive, what partitioning scheme will be the best for performance

Thanks

---

### Post by julio_cortez on 2010-08-24
How many OSs are you planning to use? I can tell you how I partitioned my 2 PCs if it can be helpful..

OLD PC (40GB IDE disk, only Kubuntu 9.10)```

hda1: 20GB ext4, /
hda2: 18GB ext4, /home
hda3:  2GB swap
```CURRENT PC (1TiB SATA disk, W7 + Ubuntu 10.04)```

sda1: 250GB NTFS, W7 (C:\ drive, of course)
sda2: 500GB NTFS, Data (shared between OSs. D:\ in W7, /media/Data in Ubuntu)
sda4: 100GB ext4, /home
sda5:  85GB ext4, /
sda6:   8GB swap
```

---

### Post by martinr on 2010-08-24
First allocate a SWAP partition, then your main partition.
Allocate at leas as much SWAP space as there is physical memory in your machine (it is used for hybernation too, ideally choose twice as much swap than physical memory, but this may not hold any more now that physical memory size has grown very big over the past years).

This way the disk head movements between the swap partition and your main programs will be minimal. Furthermore the first sectors on the disk are the fastest, so best suited for memory swapping.

---

### Post by eithantlv on 2010-08-24
This 130GB of space is for Linux only (windows on other drive)
So, out of 130GB (with 2 GB RAM) will it be good partitioning:
swap 4 GB
/home 80 GB
/ 46 GB

---

### Post by julio_cortez on 2010-08-24
If you have Windows on another drive, maybe you can consider adding a small NTFS partition that is "shared" between the OSs, just in case..

---

### Post by Paqman on 2010-08-24
> **eithantlv said:**
> This 130GB of space is for Linux only (windows on other drive)
So, out of 130GB (with 2 GB RAM) will it be good partitioning:
swap 4 GB
/home 80 GB
/ 46 GB

That would do, although your swap only needs to be 2GB if you're using hibernation (aka suspend to disk), otherwise it doesn't even need to be that big. Modern systems with more than about 1GB of RAM don't really use swap except during hibernation.

---

### Post by martinr on 2012-06-15
> **Paqman said:**
> That would do, although your swap only needs to be 2GB if you're using hibernation (aka suspend to disk), otherwise it doesn't even need to be that big. Modern systems with more than about 1GB of RAM don't really use swap except during hibernation.
Oh, don't forget to add an extra 200MB (from memory, could be 64KB also?) to swap. It has some overhead thing going.

---

