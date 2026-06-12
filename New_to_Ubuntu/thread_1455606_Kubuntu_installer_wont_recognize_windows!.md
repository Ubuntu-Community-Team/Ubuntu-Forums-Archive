---
title: "Kubuntu installer wont recognize windows!"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by ni_ko on 2010-04-16
I decided to re-do my net book today so i reformatted everything and did a clean install of windows 7. Now when running the kubuntu 9.10 installer, instead of asking if i want to install side by side, it says no other operationg system is on this disk. IT SAYS MY HD IS EMPTY!!!

---

### Post by zvacet on 2010-04-16
You can try to make partitions with [Gparted live CD.]("http://gparted.sourceforge.net/") If you want you can make separate home partition,because that way you will be able to do fresh install or something similar in future without delete your settings/data.So with Gparted make root,home (optional) and swap.Format is ext4.Boot Kubuntu Cd again and it should recognize ext4 partition.Install Kubuntu on that partition.

---

