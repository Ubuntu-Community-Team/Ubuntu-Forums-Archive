---
title: "Gparted - Partitioning Question"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by sharks on 2010-01-24
Hmm. Hello. I have Ubuntu 9.04 . I have two HDD's. One is the default one which came with the system. I bought a new HDD of 500 GB. Now I would need to partition the 500 GB HDD. 

I installed Gparted. Then when I select HDD2 (500 GB) , it shows Delete, Format to Ext2,3,etc except NTFS ( I believe its already formatted in NTFS). Now I need to partition it. But the "New" option is blocked/de-selected. So, I have delete option. Not sure of whether I should use it and then will it allow me to create new drives?

Regards,
Sharks

---

### Post by J V on 2010-01-24
output fdisk -l plz

Edit: Ah yes, ubuntu can't format NTFS, but if you want to delete it and create ext partitions, go right ahead...

---

### Post by howefield on 2010-01-24
Try opening Synaptic Package Manager and install ntfsprogs.

This should give gparted the ntfs functions that are currently missing.

---

### Post by sharks on 2010-01-24
Okay. Cool. Thanks.

The main question, remains, If I delete the HDD (Empty), Will I be able to create new drives with it? :D

Thanks,
Sharks

---

### Post by J V on 2010-01-24
no, but you will be able to create new partitions...

If I could make new drives out of thin air I'd be rich :P

---

### Post by sharks on 2010-01-24
Okay. Tks again. :)

Doing it now.

P.S. Good to be back at the community here. Have been managing an Online Pokemon game for a year.

---

### Post by howefield on 2010-01-24
> **J V said:**
> Edit: Ah yes, ubuntu can't format NTFS,...

Not out of the box, but with ntfsprogs, you can.

---

### Post by candtalan on 2010-01-24
> **sharks said:**
> Okay. Cool. Thanks.
The main question, remains, If I delete the HDD (Empty), Will I be able to create new drives with it? :D 

A drive is firstly partitioned then each partition is formatted. The partiton serves to provide boundaries, and the formatting creates a file system structure within the boundaries.

In Windows, a partition is shown as a 'drive', for example, drive C. This is potentially confusing, and if a novice user starts to get curious, then here is an initial confusion to 'remind' the user to just do what the Company says, and not to meddle (!)

In freedom software, drives are devices and are given alphbetical names. The first drive will be device hard drive a
/dev/hda
and partitions in it will be numeric. Two partitions in hard drive a will be
/dev/hda1
/dev/hda2

Having said that, it is usual nowadays that hard drives are recognised not as hda but as sda (originaly scsi drive a) 

hth

---

### Post by sharks on 2010-01-24
Thanks to all but just when I deleted the HDD, my system went off totally (It had no content before . :D) Don't know why but still, I am not gonna risk again. Thanks to all.

---

### Post by luffy_chan_19 on 2010-01-24
what you do in this case if it will not let you delete the partition on the drive is (in Gparted) just click Device->create new partition table. this should work around this slight problem. no need in installing any extra crap. this is how i reformatted an ntfs formatted drive on my system

---

