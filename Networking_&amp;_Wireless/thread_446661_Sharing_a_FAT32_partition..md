---
title: "Sharing a FAT32 partition."
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Zigosity on 2007-05-17
Is it even possible to share a FAT32 partition from Ubuntu? If it is, could someone please show me how? I've been trying all week. It seems to be impossible to set permissions on the drive, because it's FAT32, so I can't get it to share.

Thanks.

---

### Post by Wim Sturkenboom on 2007-05-17
Not sure what your problem is. Any Linux user can access the FAT32 partition, if the proper permissions are set in fstab; so maybe your problem is there.

Don't have Ubuntu at hand at this moment to check.

---

### Post by Zigosity on 2007-05-17
I'm trying to share the FAT32 partition with a windows PC with samba. When I try and set permissions in fstab it gives me an error on boot and won't mount the drive. I've also tried setting permissions everywhere else, including in nautilus and from the terminal, as root, but it won't budge from the current settings...

---

### Post by merlinus on 2007-05-17
Maybe you should use NTFS.  It is far more secure than FAT32, and with the ntfs-3g tool installed (available from Add/Remove Applications), Ubuntu can read and write to it with zero problems.

Then on the windows side you can install ext2IFS if you want that OS to read ext3 partitions.

-merlin

---

### Post by Zigosity on 2007-05-17
I finally fixed it, just now... Found a much easier (And sort of better, hurrah!) way:

Instead of mounting the drive into /media, the default place, I mounted it into another folder which I had already set permissions for. The whole system works perfectly! Hurrah! =P

---

