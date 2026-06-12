---
title: "lost+found folder (what is it for?)"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by crjackson on 2009-01-17
I decided to reformat one of my auto-mounted NTFS drives to ext2 and use it exclusively for Linux files. After doing this I had to edit my fstab, and chown, chmod and such and now I can see the drive and write to it.

I notice it came equiped with a folder in the root directory called lost+found. What is this folder? Do I need it? Can I safely hide it somehow?

Thanks for any information.

---

### Post by ac7ss on 2009-01-17
Do not delete it, it is part of the EXT2-3 file system. That is where files recovered without directory information will end up on a disk check. You may safely ignore it unless you are missing a file after a mount scan.

---

### Post by crjackson on 2009-01-17
> **ac7ss said:**
> Do not delete it, it is part of the EXT2-3 file system. That is where files recovered without directory information will end up on a disk check. You may safely ignore it unless you are missing a file after a mount scan.

I figured it would be something like that. Thanks:KS

---

