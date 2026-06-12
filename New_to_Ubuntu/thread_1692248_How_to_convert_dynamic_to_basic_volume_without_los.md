---
title: "How to convert dynamic to basic volume without losing data?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by apple2user on 2011-02-21
Is there a program to do the conversion in Ubuntu? Something equal to Partition Wizard Pro in Windows.

---

### Post by oldfred on 2011-02-21
Welcome to the forums. But it is really more of a windows question.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)

---

### Post by apple2user on 2011-02-24
Finally got it.

Option 1 - delete partitions and repartition
Only as a last resort and thankfully not necessary!

Option 2 - testdisk
Tinkered around with it for past two days. It did not work in my case because my hard disk was divided into 2 partitions. testdisk can convert ONE partition to a basic partition (meaning the second dynamic partition would have been lost). I considered copying all the files into one partition and converting that into a basic partition; then deleting the other partition. In the end did not have to do that because of the final option (see below). Would have taken hours to copy a few hundred gigabytes of data...

Option 3 - Partition Wizard
Free edition cannot do the conversion (I would rather spend the money towards an external hard disk).

Option 4 - EASEUS Partition Master
The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!

Btw, this was actually a combined Windows/Ubuntu problem because I was trying to stay away from Windows and solve the problem in Ubuntu. Thanks for your suggestions.

---

### Post by Mina Fouad on 2011-12-22
Is there a bootable software to perform this task, windows is down :(

---

### Post by oldfred on 2011-12-22
Whatever you decide to use be sure to have good backups first.

Partition Wizard has a newer free version MiniTool that also has a full liveCD version (bottom of page last time I looked).

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

It looks like EASEUS Partition Master also has a bootable CD version(s). WinPE or Linux with the WinPE version having more features. I cannot tell is the free is bootable or only the paid versions.

---

