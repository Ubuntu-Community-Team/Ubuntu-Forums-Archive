---
title: "Windows not booting after Ubuntu install"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by anubhav.sharma on 2010-12-06
Hi All,
 
I am facing bit similar problem. I have installed ubuntu 10.10 on my machine along with windows 7. My hard disk had 4 partitions as follows:
[LIST]
[*]25 GB NTFS WINDOWS7
[*]10 GB UNALLOCATED
[*]75 GB EXT4
[*]50 GB EXT4
[/LIST] 
After installing the ubuntu my windows7 has crached and the 1st partition is now cleaned by ubuntu. Moreover, the ubuntu is also not working properly (means I don't get the login screen). Now I want to re-format my whole hard disk with NTFS only for WIN7 but I am unable to format my hard drive as none of OS is working.
 
Please help me, I am in trouble as I can't use my PC. 
 
Thanks,
Anubhav

---

### Post by Quackers on 2010-12-06
Ajay Ramaseshan,
the maximum number of primary partitions on any disc is 4.
If you want to install another operating system you should reduce the number of primary partitions to 3 and then create an extended partition. Then you can have as many logical partitions as you want within that extended partition.
Be careful which partitions you delete though. You don't want to trash your Windows system!

---

### Post by Quackers on 2010-12-06
anubhav.sharma
you should start your own thread giving full details of what has happened.

---

### Post by overdrank on 2010-12-06
Hi and welcome. Moved your post and the responses to its own thread. :)
Thread closed. [Duplicate here]("http://ubuntuforums.org/showthread.php?t=1638846").

---

