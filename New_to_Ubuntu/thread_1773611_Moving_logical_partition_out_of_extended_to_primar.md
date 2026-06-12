---
title: "Moving logical partition out of extended to primary"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by mivadar on 2011-06-02
I have the following partition table:

sda1 (primary) NTFS
sda2 (extended), containing
sda5 (logical) FAT32
sda6 (logical) linuxswap
sda7 (logical) ext4

I have linux installed on sda7, windows on sda1.

I would like to kill my windows install and unite the space of sda1 and sda5 into a single partition, format with ext4 and use in linux - without reinstalling ubuntu on sda7.

That is, I would like to move sda5 out of the extended partition, wipe both sda1 and sda5 and unite them, without touching sda6 and sda7.

Is this possible?

---

### Post by coffeecat on 2011-06-02
> **mivadar said:**
> 
That is, I would like to move sda5 out of the extended partition, wipe both sda1 and sda5 and unite them, without touching sda6 and sda7.

Is this possible?

Not in the way you describe but, in essence, yes - so long as the partitions you listed do physically appear in that order on the disk. You need to:

Delete sda1 and sda5. Resize (shrink) the extended partition sda2 so that it releases the space formerly occupied by sda5. Then create a new primary partition in the unallocated space freed by deleting sda1 and sda5.

Caveats and warnings. Do this using Gparted from the live CD, and choose "swapoff" by right-clicking on the swap partition, otherwise your extended partition will be locked. And usual warning about working on partitions. Backup, backup and backup again. Things can go wrong.

**EDIT**: just noticed you're using Kubuntu. I'm not sure whether Gparted or a qt-based GUI parted app comes with Kubuntu, but use whichever *parted there is.

---

### Post by mivadar on 2011-06-02
Thanks, I'll try.

(The partitions are in the order listed - I made them this way because I anticipated that I would eventually merge sda5 with either the windows or the linux partition, so I put it in the middle.
I was counting on having 4 partitions, all primary - but Windows messed up my beautiful plan by blocking a 8 MB piece at the end of the drive, so I had to make at least two partitions logical. Retrospectively it was stupid not to have the FAT32 as a primary.)

---

