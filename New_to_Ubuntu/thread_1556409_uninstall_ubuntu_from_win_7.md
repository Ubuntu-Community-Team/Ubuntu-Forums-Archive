---
title: "uninstall ubuntu from win 7"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Sasman20 on 2010-08-19
I have grub installed on my Windows 7 laptop dual booted with Ubuntu, I want to uninstall ubuntu. I understand that I have to restore the master boot record but have not been able to do so after following the instructions from a windows forum. 
 
If I uninstall ubuntu from add remove in Windows 7 will the partitioned space be restored? How do I modify the mbr and safely remove Ubuntu
 
 
Suggestions greatly accepted
 
Sas

---

### Post by elliotn on 2010-08-19
U need to format the ubuntu partition and use your win7 cd to fix windows mbr

---

### Post by Trinity33 on 2010-08-19
> **Sasman20 said:**
> I have grub installed on my Windows 7 laptop dual booted with Ubuntu, I want to uninstall ubuntu. I understand that I have to restore the master boot record but have not been able to do so after following the instructions from a windows forum. 
 
If I uninstall ubuntu from add remove in Windows 7 will the partitioned space be restored? How do I modify the mbr and safely remove Ubuntu
 
 
Suggestions greatly accepted
 
Sas

u should delete partition with ubuntu under windows in control panel administrative tools disk and than delete partition with ubuntu extend win7 disk and close it. u need win 7 cd to be able to restore everything if u dont u wont be able restore mbr. so if u delete grub u wont be able to boot up windows if u have win cd then instert it and follow those websites
  


check up this [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

and i used that one [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by elliotn on 2010-08-19
Oh ya type FixBoot in command line and it would write a new boot record in your partition

---

### Post by halitech on 2010-08-19
by the sounds of it, you used WUBI to install Ubuntu. If you remove it from Add/Remove then it *should* revert all the settings when you do so. Also, with a WUBI install, your drive isn't really partitioned so you don't need to format anything, its just placed inside a quasi-partition as a file inside C:\Program Files\Ubuntu (or where ever you installed it to)

---

