---
title: "whats the command line to see the all the specs?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-06-02
i was just curious what are the specs of this server that i am connected to via shh.

what is the command to tell what kind of specs the server is running?
you know like harddrive space, what hardware it is using.

---

### Post by cak3 on 2009-06-02
Well, I know there is a package called hwinfo that can do that, but It would either have to be installed on the server or else you would need permission to install software...

in any case, you can simply install it via apt-get if you have permission:
```
sudo apt-get install hwinfo
```

I also know that he command df reports free HDD space
use ```
df -h
``` to output it in a human readable format (hence the -h flag). 

```
cat /proc/cpuinfo
``` should give you the cpu info, assuming you have read permissions for /proc, or at least that file. 


I don't know of a single, built-in command to see the specs though.

---

### Post by y@w on 2009-06-02
Adding to that:
```
cat /proc/meminfo
```

will show the memory information.

---

### Post by Toshubu on 2009-06-02
> **shiningkenmonster said:**
> i was just curious what are the specs of this server that i am connected to via shh.

what is the command to tell what kind of specs the server is running?
you know like harddrive space, what hardware it is using.

Try lspci and lsusb.

---

### Post by nhasian on 2009-06-02
what?  no one suggested lshw?

```
sudo lshw
```

---

### Post by lisati on 2009-06-02
There are many ways of learning what's "under the hood". To the other suggestions I add: ```
sudo dmidecode
```

---

### Post by s.fox on 2009-06-02
Hi,

I found [this]("http://ubuntuforums.org/showthread.php?t=884431") thread in the archive.

Hope it helps you.

-Ash R

---

