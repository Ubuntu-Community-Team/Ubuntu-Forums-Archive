---
title: "Uninstalling Ubuntu From Duel Boot With Windows 7???"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by wpwend42 on 2010-05-03
Been running Ubuntu since 2007...finally buying a new laptop later this week, which will have Windows 7 on it. I want to duel boot Win7/Ubuntu 10.04. HOWEVER, if I wanted to delete Ubuntu from it, how do I go about doing so? In the past, I have just written over the entire drive when installing a fresh version of Ubuntu, so doing this while duel booting is new to me. Thanks!

---

### Post by nitstorm on 2010-05-03
ubuntuforums.orgubuntuforums.org/newreply.php
When you delete the Ubuntu partition, the Grub or Grub-2 also goes bye-bye along with it so you'll have to restore the MBR back.
Here are a few links:
[http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/](http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/)
[http://www.blogsdna.com/6091/repair-the-mbr-to-restore-windows-7-to-multi-boot-options.htm](http://www.blogsdna.com/6091/repair-the-mbr-to-restore-windows-7-to-multi-boot-options.htm)

---

### Post by cap10Ibraim on 2010-05-03
I did this before with 9.10 (i removed it) , but now i dual boot with 10.04 again 
but here is how I deleted Ubuntu 
I made a windows 7 rescue disk from the backup options in windows 7 control panel 
I used disk management (in windows7) to delete Ubuntu partitions 
now grub is corrupted ! 
so Insert and boot the rescue disk then you will see an option to run command prompt 
type : 
[FONT='Courier New'][I]Bootrec.exe/FixMbr
**[SIZE=4][FONT=Arial Narrow]reboot everything will be fine [/FONT][/SIZE]**
[/I][/FONT]

---

