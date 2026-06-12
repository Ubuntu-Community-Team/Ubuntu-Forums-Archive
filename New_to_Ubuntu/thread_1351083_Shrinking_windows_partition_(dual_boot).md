---
title: "Shrinking windows partition (dual boot)"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Sejanus on 2009-12-10
I've got dual boot Ubuntu 9.04/Vista. I need to reinstall Vista and this time I'd like to leave far less space for it, e.g. to shrink that partition and to expand Ubuntu partition at windows expense. Is it possible to do without reinstalling Ubuntu as well?

Also, I've got two disks C: and D: (in Windows terms), both OS are hosted in one of them (C) and another one (D) can be seen by either. I'd like to make it so that Vista will not see it in any way or form anymore, e.g. reserved for Ubuntu only :) Exactly like Vista does not see current Ubuntu partition now. Is it possible?

Thanks in advance for your help and sorry for noobish question :)

---

### Post by oldfred on 2009-12-10
If you are totally reinstalling you can ignore some of the advice on these links but Vista and Win7 did change the starting sector from 63 to 256(?). You can use gparted to shrink the NTFS partition and expand an adjacent partition, but without knowing your layout that may or may not be the Ubuntu install partition. If you are making a lot of room you can add a data partition but be careful of any renumbering of partitions & UUID's that will required manual editing of fstab or grub reinstall. You install of Vista will probably require a reinstall of grub anyway. If you can backup your D: drive and reformat it to ext3 or ext4 windows will not see it and it can be a data partition in Ubuntu. 

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Windows Disk Cleanup tool to houseclean
defrag at least twice
#Partitioning generally better
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by Sejanus on 2009-12-11
> **oldfred said:**
> If you are totally reinstalling you can ignore some of the advice on these links but Vista and Win7 did change the starting sector from 63 to 256(?). You can use gparted to shrink the NTFS partition and expand an adjacent partition, but without knowing your layout that may or may not be the Ubuntu install partition. If you are making a lot of room you can add a data partition but be careful of any renumbering of partitions & UUID's that will required manual editing of fstab or grub reinstall. You install of Vista will probably require a reinstall of grub anyway. If you can backup your D: drive and reformat it to ext3 or ext4 windows will not see it and it can be a data partition in Ubuntu. 

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Windows Disk Cleanup tool to houseclean
defrag at least twice
#Partitioning generally better
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Weird, a bit ago I wasnt able to find this thread so I assumed it got deleted due to some rules breaking from my part or something :( Thanks for your advice but I already did it in my newbish way :) I hope didnt [mess everything up]("http://ubuntuforums.org/showthread.php?t=1352161") too much...
*goes to read given articles* thanks again oldfred

---

