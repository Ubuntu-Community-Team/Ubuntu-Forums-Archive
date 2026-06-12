---
title: "how to add more space"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by all4enjoy on 2009-09-08
hi i installed ubuntu 9.04 on my system..
 
windows was previously installed in that...my HDD space is 238GB
 
there are five partitions each consist of 40GB or more ..
 
i installed ubuntu as side by side (i.e. dual boot)..
 
then i downloaded some themes for my new ubuntu ..after completing 22% it shows an error that
 
"there is no more space " . so i cancelled it and asking for help that 
 
"how to increse my ubuntu OS size " plz help me ....
plz
 
 
and also i cant able to access root folder .but i am an administrator why so..
 
reply me in detail ..
waiting for your help

---

### Post by credobyte on 2009-09-08
**# Resize partition**
Boot from your Ubuntu LiveCD and use Gparted ( System / Administration ).

**# Access file system - root directory**
```
gksudo nautilus /
```

---

### Post by Zoot7 on 2009-09-08
Yup Gparted is your best bet as all4enjoy says.

Just be sure to back up everything essential before you go resizing partitions. ;) And if you've to resize an ntfs partition defrag it a couple of times before you resize it, otherwise it could take hours.

---

### Post by egalvan on 2009-09-08
Take a look at this thread...

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

