---
title: "Virtual Drive"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by RealG187 on 2010-01-05
I have a USB Drive formatted to FAT32 that I do not want to convert to NTFS (Compatibility with my [NSLU2]("http://bestwikiever.wikidot.com/NSLU2")) but I need to copy some files to it that are larger than 4 GB.

Is there a way I can make a virtual drive on it, so I can copy the 4 GB file to it and have them stored automatically in a bunch of smaller files?

I would need something that works on Windows and Linux...

I could RAR/Zip/7-Zip them, but it would be nice if there was a program that did this automatically...

---

### Post by starcraft.man on 2010-01-05
I get what your saying, but er no, I don't think so. Just ponder a moment, that a virtual drive that was more able to hold more than 4GB would itself be a file breaking the FAT32 limit. You could make another partition on the drive, that partition could be hard or lvm (a form of virtual partitioning) but no, you can't just make a virtual space inside of fat32 easily to my knowledge that spans the limit in a single space. 

If someone does know some interconnected spanning drive up to 4gb sections that would be awesome though I am skeptical.

Can't just gparted the drive to have an NTFS section for this storage? Alternatively a pendrive just for ntfs/other FS. Just my thoughts.

If you go the archiving route, I like 7-zip if ya got the CPU for the intense/long compressing.

---

### Post by RealG187 on 2010-01-05
The virtual drive wouldn't be breaking the limtits if it was in a bunch of smaller files. I think I can make VMDKs span files, but then I would have to run a VM to access the drive...

---

### Post by Methuselah on 2010-01-05
Are you talking about something like HJSplit or lxsplit?
I guess not because I think you want them automatically split or joined.

With some coding that could probably be accomplished with a combination of those programs and FUSE (file system in user space).
I don't know of an existing solution though.

---

