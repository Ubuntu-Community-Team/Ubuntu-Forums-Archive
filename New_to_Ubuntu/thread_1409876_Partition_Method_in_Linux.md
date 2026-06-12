---
title: "Partition Method in Linux ?"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by honey_bee on 2010-02-18
Hi,
     I am new in Linux. I to know the partition method in linux.  Normally in windows we install the OS like windows XP  on C Drive.To  install rest of the software like Ms office I keep it away from my C  drive in install in D drive. In my Last drive I keep all of my personal  data  in it.
      The benefit of doing this that i keep the operating system in a  separate partition,User software in a separate partition and   my  personal thing in an other separate partition.

Keeping in view the above in Linux how can i keep my operating system  partition separate and my personal data?


honey

---

### Post by da burger on 2010-02-18
I think this link might be what you are looking for:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by louieb on 2010-02-18
Separate your data from the OS - yes. When i install Linux or windows for that matter I use a separate partition for my data. 

One difference in windows each partition is accessed through a drive letter c: e: f: ... With Linux your data partition(s) become another branch in the fie-system tree. Access is through their mount point. Typically I make my mount points /media/data , /media/stuff , ... - then create links on the desktop for ease of access. 

Its a lot different from using windows, but once you get use to it - it becomes really simple.

---

### Post by ghmanek on 2010-02-18
Separateing your data from the OS is very important...

---

### Post by audiomick on 2010-02-18
One thing: As far as I know, you can't specify where programs are installed to, and don't need to. You should make sure that the partition that / is on, that is where the OS and programs are, has room to grow. With a separate /home partition for my data and users settings, I have around 6GB in /. If you are short of drive space, think about 10 to 15 GB, if you have plenty of space, give it 20GB or so. That should be ok for the next several years at least.

---

