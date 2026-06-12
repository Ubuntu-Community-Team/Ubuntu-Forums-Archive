---
title: "Trouble with suspend to disk"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by pete-the-meat on 2009-02-07
I am having trouble suspending to disk (to ram works fine) - when I try to do it the console informs me that it can't find the swap device and to try swapon -a (which has no effect). I am clueless as how to continue from here.

Any help?

Thanks :)

---

### Post by avtolle on 2009-02-07
Do you have a swap partition, and, if so, is it at least as large as the RAM installed on your computer? If you are using a swap file instead, someone else will surely have a suggestion for you.

---

### Post by HavocXphere on 2009-02-07
Weird. Is there a swap mentioned in your fstab file? (/etc/fstab)

---

### Post by pete-the-meat on 2009-02-07
Well I created a swap partition of 1Gb since I have 1Gb memory and used

pete@peyote:~$ swapon -a /dev/sda3
pete@peyote:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda1                               partition       2096440 22720   -1

and tried hibernating but it gave me that message. /dev/sda3 is a 1Gb swap partition - I have 1Gb of RAM working on an advent 4213 netbook.

---

