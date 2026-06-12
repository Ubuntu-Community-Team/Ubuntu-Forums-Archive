---
title: "whenever i put in a CD, it says &quot;unable to mount drive&quot;"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by hyperhopper on 2009-06-13
whenever i put in a CD, it says "unable to mount drive" no media detected.


what should i do

---

### Post by TeoBigusGeekus on 2009-06-13
Try 
```
sudo mount /dev/scd0
```
or whatever your cdrom is called.

---

### Post by hyperhopper on 2009-06-13
how do i find what its called?

---

### Post by TeoBigusGeekus on 2009-06-13
Look at your fstab file
```
sudo cat /etc/fstab
```

---

### Post by hyperhopper on 2009-06-13
```
 sudo cat /ect/fstab
cat: /ect/fstab: no such file or directory 
```

---

### Post by TeoBigusGeekus on 2009-06-13
> **hyperhopper said:**
> ```
 sudo cat /ect/fstab
cat: /ect/fstab: no such file or directory 
```
```
etc
```
not 
```
ect
```

Mea culpa.

---

### Post by drs305 on 2009-06-13
You have a typo:
> sudo cat /[COLOR="Red"]ect[/COLOR]/fstab

It's "cat /**etc**/fstab"

---

### Post by hyperhopper on 2009-06-13
```
#/etc/fstab: stactic file system information
#
#<file system> <mount point> <type> <options> <dump> <pass>
proc              /proc         proc    default 0      0
# /dev/sda
UUID=f4fe72e7-817a-44f9-43a8990c48c5/   ext 3   realtime, error
S=remount-ro    0     1
#/dev/sdas
UUID= asace0a56-2589-488a-9b62-6a6135ad822f none swap sw
0    0
/dev/scd0   /media/cdrom0   undf,iso9660, user, noauto, executf8,    0   0
/dev/fd0  /media/floppy0    auto, RW, user, noauto, executf8,    0   0 
```

---

### Post by TeoBigusGeekus on 2009-06-13
So it's /dev/scd0.
Try
```
sudo mount /dev/scd0
```

---

### Post by hyperhopper on 2009-06-13
```
 mount: no medium found 
```

---

### Post by TeoBigusGeekus on 2009-06-13
Ok.
Have you tried with a lot of cds?
Can it mount dvds?
How about data disks?
Perhaps it's a hardware failure - is the drive old or new?

---

### Post by hyperhopper on 2009-06-13
nope, not loading anything... it was working a week ago....

maybe i can switch an identical cd rom drive from another computer of the same model that i have?

---

### Post by TeoBigusGeekus on 2009-06-13
Yeah sure, do it. Perhaps the drive has died on you.

---

### Post by hyperhopper on 2009-06-13
thx, its working now... cya!

---

