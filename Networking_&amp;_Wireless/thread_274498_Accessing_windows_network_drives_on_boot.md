---
title: "Accessing windows network drives on boot"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by killerpie666 on 2006-10-09
Hi, i'm a bit new to this. I am running Dapper Drake and i've already been to the forums and found an answer. 
I am trying to mount my windows network drives on boot.
i sucessfully modified my /etc/fstab/ file and i have icons on my desktop for the mounted drives but when i try to open the drives it says that only root may access them.

How do i fix this?

this is my /etc/fstab/

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda2 /media/sda2 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
//AZURIEL/I     /mnt/I     smbfs     defaults,uid=<xxxx>,username=xxx,password=xxx     0     0
//AZURIEL/D     /mnt/D     smbfs     defaults,uid=<xxxx>,username=xxx,password=xxx     0     0
//ZARIEL/I     /mnt/F     smbfs     defaults,uid=<xxxx>,username=xxx,password=xxx     0     0

---

### Post by koshari on 2006-10-10
i have had more success using cifs in my fstab file, 

i could post my entry when i get home,

---

### Post by psychobillyjekyll on 2006-10-18
You can sudo chmod -R 777 //Computer/folder and that should give you permission to do as you wish with the files.

---

