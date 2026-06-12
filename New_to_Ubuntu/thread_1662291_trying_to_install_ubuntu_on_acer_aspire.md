---
title: "trying to install ubuntu on acer aspire"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by robbbie on 2011-01-07
I have an acer aspire netbook with windows XP.I put ubuntu on a usb drive .Everything is fine.Tried Ubuntu and now want to install it.The problem is when I get to the page where you set the amount for the partition it says there is a small hidden partition(pqservice about 6 gig) so I have to use the advanced option to set a partition.This is the problem.I am nervous about losing xp and all my files.I want to be able to use either OS.How do I set the partition on the Acer to continue with the install?Thanks

---

### Post by JC Cheloven on 2011-01-07
That small partition is surely a recovery area, to eventually get back the computer to the factory status. So you don't want to delete it.

Please, from your live session open a terminal, type ```
sudo fdisk -l
``` select with the mouse the output, hit ctrl-shift-C to copy the selected text, and paste it back here.

---

