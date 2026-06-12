---
title: "is it safe to uninstall ubuntu in this manner ?"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by naved ..... on 2011-05-15
hii , i want to uninstall ubuntu 10.10 frm my pc which already had win 7 
but before installing ubuntu i had created restore point ..so if i put my pc in that point of time so can this is possible ?
1.will all the ubuntu files get deleted and space allocated to it will be given back to win 7 as it was earlier 
2.grub will be gone and ,  win7 bootloader will be installed back in mbr 
3. can i will be safely able to log-in to win7 without any problem of bootloader or anything else could possibly happen ?
plz help 
thnx

---

### Post by jerome1232 on 2011-05-15
No, a restore point won't do anything to affect the bootloader or Ubuntu.

How did you install Ubuntu, is it Wubi or a real dual boot.

If it was a Wubi install you can just remove it from add/remove programs.

If it is a dual boot you need to restore the mbr (easybcd is an easyway to do this) then use the Windows disc manager to delete all Ubuntu partitions, then resize your existing Windows partition to take the space back.

---

### Post by naved ..... on 2011-05-16
> **jerome1232 said:**
> No, a restore point won't do anything to affect the bootloader or Ubuntu.

How did you install Ubuntu, is it Wubi or a real dual boot.

If it was a Wubi install you can just remove it from add/remove programs.

If it is a dual boot you need to restore the mbr (easybcd is an easyway to do this) then use the Windows disc manager to delete all Ubuntu partitions, then resize your existing Windows partition to take the space back.

can i restore the win 7 bootloader by clicking on install windows vista/7 bootloader and followed by clicking on write mbr.
and than i have to delete the partition of linux through any partition maneger 
see the following image for details ....

is the above method which i had said u is correct and i ll not face problem  ha  ?

---

### Post by jerome1232 on 2011-05-16
Yup, looks good, the Windows Disk Utility should be under Control Panel-Administration Tools-Computer Management-Disk Management.

Be sure your deleting the correct partition ;). It's generally a good idea to have a backup handy in case a random act of chaos happens when your messing with partitions.

---

### Post by naved ..... on 2011-05-17
> **jerome1232 said:**
> Yup, looks good, the Windows Disk Utility should be under Control Panel-Administration Tools-Computer Management-Disk Management.

Be sure your deleting the correct partition ;). It's generally a good idea to have a backup handy in case a random act of chaos happens when your messing with partitions.
  after installing win7 bootloader to mbr(using easybcd app) do i need to restart my pc ...bcoz it ll be better to see wheather bootloader of win7 is working , i believe if it ll work , then i ll be not prompt with grub bootloader of linux any more... and my win7 ll suppose to start directlly though linux ubuntu is present in hdd...? write or wrong ?
plz give ur opinion

---

### Post by jerome1232 on 2011-05-17
correct.

---

