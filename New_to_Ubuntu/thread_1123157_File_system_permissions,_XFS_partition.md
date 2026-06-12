---
title: "File system permissions, XFS partition"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Zeedok on 2009-04-11
I am using a new Mythbuntu system - with an ubuntu desktop - and the chap who built it for me only allocated 11GB to the primary partition.  I have 1TB in total, but on the ubuntu-desktop side I do not have permission (nor do any programs I run) to use that space.

The majority of my hard drive is partitioned as XFS, which cannot be shrunk - I know I could repartition it, but that would probably lead to a complete reinstall of mythbuntu - not something I am looking forward to.  I figure, if I could just get permission to use the XFS section of my hard drive when I really need the space, then I could make do.

How can I do this?

Thanks for any suggestions.

---

### Post by camnor on 2009-04-25
Hey! 
What you can try to do is use a live cd to open GPARTED and deleted the XFS section of the drive and just grow your 11gb partition, or you can try mounting the partition IF it shows up in gparted under your Sys Admin menus.

Hopefully that helped~!

---

