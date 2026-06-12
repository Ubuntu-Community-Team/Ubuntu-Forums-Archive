---
title: "GUI program to open harddisk with several type partitions?"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-12
Hi, I have made a **[COLOR="Red"]dd[/COLOR]** of a harddisk. THere is 1 or 2 partitions aout of 6 that have crashed. I would like to explore this image of harddisk altough some partitions are not redeable and can be studied with photorec if possible. 

(dd to backup a disk : [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm) )

Mount is not working on those. Is there a program to open harddisk images with partitions in it? Soemthing like isomaster but for dd images?

thank you

---

### Post by srs5694 on 2010-09-12
What was the target? If you did the dd copy to another hard disk, then it should be accessible just like any disk, although with the caveat that the system may get confused by the fact that the UUID numbers (sort of like a serial number) for two partitions (the original and the backup) are identical, so you may need to mount the partitions manually using mount, as in:

```

sudo mount /dev/sdb3 /mount/point

```

Change /dev/sdb3 to whatever partition you want to change, and change /mount/point to a suitable empty directory to be used as a mount point.

If you've made a copy to a disk file, then the following script might help. Copy-and-paste it into a file (say, mount_image), save it, and then type "chmod a+x mount_image" to make it executable. As noted in the comments, the script relies on my GPT fdisk (gdisk) program, so you'll need to install it first. Use it like "sudo ./mount_image image_file 3 /mount/point", where image_file is the image file, 3 is the partition number, and /mount/point is the mount point.

```

#!/bin/bash

# mount_image, a program that mounts a specific partition from a RAW
# disk image file, such as a full-disk dd copy or a file used by QEMU.
# Note that compressed and other space-saving formats (qcaw2, etc.)
# will NOT work!

# Use:
# mount_image image_file partition_number mount_point
#
# For instance,
#
# mount_image image.raw 2 /mnt/shared
#
# mounts partition 2 from image.raw at /mnt/shared.

# This program relies on my GPT fdisk (gdisk) program to help identify
# partitions. I could have used regular fdisk, but this would have
# limited the program to working with MBR-formatted disks. With gdisk,
# both MBR- and GPT-formatted disks will work.

gdisk -l $1 > /tmp/mount_image.tmp
let StartSector=`egrep "^   $2|^  $2" /tmp/mount_image.tmp | fmt -u -s | sed -e 's/^[ \t]*//' | head -1 | cut -d " " -f 2`

let StartByte=($StartSector*512)

echo "Mounting partition $2, which begins at sector $StartSector"

mount -o loop,offset=$StartByte $1 $3

rm /tmp/mount_image.tmp

```

---

