---
title: "Ubuntu could not open location 'file/home/zxn/Disk_D"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by 2mazda on 2010-12-21
Der sirs, 
Although I have used Ubuntu for over 1 year without much problem(not so stable compared with Windows XP), but since two months ago when I try to open my disc D under 'Place', I constantly encounter 'Ubuntu could not open location 'file/home/zxn/Disk_D' 'Error stating file '/home/zxn/Disk_D': Transport endpoint is not connected problem. I use dual system:windows XP and Ubuntu, and Disc: D/ is the common one for both systems(I installed Ubuntu in Disc E). My Ubuntu version is 10.04 LTS. I guess it is due to my upgrading of certain software. The strange thing is the problem sometimes does not occur. Really hopes to figure out what is wrong. Pls give me detailed instructions as I do not have much knowledge about Ubuntu.

Thanks

---

### Post by cariboo on 2010-12-21
We don;'t use disk letter designations in Ubuntu, it's usually /dev/sda1, /dev/sdb1 etc. That being said, have you tried running **chkdsk d: /f** in Windows?

---

### Post by 2mazda on 2010-12-24
> **cariboo907 said:**
> We don;'t use disk letter designations in Ubuntu, it's usually /dev/sda1, /dev/sdb1 etc. That being said, have you tried running **chkdsk d: /f** in Windows?
I can open disc D: in Windows XP without any problem. It only occurred in Ubuntu. Each time when I first log in the Ubuntu, I can open the disc under 'Computer', but sometimes after using the pc for a while when I try to open the disc, it gives me the instrcution that could not be found. Really really strange. I don't know how it can happen.

---

### Post by ryu kun on 2010-12-24
This is strange. What do following commands give?

> cat /etc/fstab

> sudo fdisk -l

> mount

---

### Post by 2mazda on 2010-12-25
> **cariboo907 said:**
> We don;'t use disk letter designations in Ubuntu, it's usually /dev/sda1, /dev/sdb1 etc. That being said, have you tried running **chkdsk d: /f** in Windows?
Thank you, sir. It seems to be working. I did just like you instructed me to run chkdsk d: /f in Windows. It seems to me that the problem comes from Windows(though apparently the Windows XP functions well all the time  but affected Ubuntu. Now it's OK. I need some time to make sure the problem will not occur again.

---

### Post by 2mazda on 2010-12-25
> **ryu kun said:**
> This is strange. What do following commands give?
Thanks for your concern. I did as Cariboo907 advised to run 'chkdsk d: /f' in Windows. Now the Ubuntu seems stable, but I still need some time to make sure the problem won't come again.

---

