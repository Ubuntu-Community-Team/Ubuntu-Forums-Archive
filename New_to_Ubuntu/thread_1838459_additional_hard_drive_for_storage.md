---
title: "additional hard drive for storage"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by hookitup on 2011-09-03
hello folks, i am running out of space on my ubuntu box so i have installed an additional 500 gb SATA hard drive in the machine, i used [DBAN]("http://www.dban.org/") and whipped the drive, and then plugged it in the second sata port on the mobo ,,, i turn the machine on , it now take twice as long to boot up, (not a big deal for me) but i can not find the hard drive under file system, where do i look for it, am i doing this correctly.?? any suggestions, ?

Thanks.

---

### Post by papibe on 2011-09-03
You can use 'Disk Utility' to format it. Here's a [guide]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/").

Optional: you can use the command line tool fdisk to do it also. [Here]("https://help.ubuntu.com/community/InstallingANewHardDrive")'s how.

Hope it helps,
Regards.

---

### Post by tsucol11 on 2011-09-03
My experience, using disk erasers, is that the HD has to be initiated before a partition can be created. You basically have a new (??) unused HD.

All my HD's were intitiated using windoze XPpro.

Read [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) on how to initiate a new HD.

Brian 

> **hookitup said:**
> hello folks, i am running out of space on my ubuntu box so i have installed an additional 500 gb SATA hard drive in the machine, i used [DBAN]("http://www.dban.org/") and whipped the drive, 
Thanks.

---

### Post by hookitup on 2011-09-03
sweet i used gparted and formatted it to ex4 and it showed up , 


Thanks ppl

---

