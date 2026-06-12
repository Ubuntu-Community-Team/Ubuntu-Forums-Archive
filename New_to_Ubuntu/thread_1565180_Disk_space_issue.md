---
title: "Disk space issue"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by sokekoke on 2010-08-31
Hello,

When i used "Disk Usage Analyser" it tells me that my total filesystem capacity is 332,3GB, and total filesystem usage is 90,0GB.

However when i go to *places > computer* and click properties on my "File system" disk it says that i only have 5.9GB free space.

how can this be? 

Thanks!

---

### Post by andrewthomas on 2010-08-31
do you have a separate partition for /home?

---

### Post by mapes12 on 2010-08-31
Worth a look:-

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by sokekoke on 2010-08-31
> **andrewthomas said:**
> do you have a separate partition for /home?

No. But i have a mounted NTSF partition, that is listed under filesystem/media/


> **mapes12 said:**
> Worth a look:-

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Thanks, will read through it soon.

---

### Post by andrewthomas on 2010-08-31
> **sokekoke said:**
> No. But i have a mounted NTSF partition, that is listed under filesystem/media/




That should make no difference.

---

### Post by bhaverkamp on 2010-08-31
Yes it does. Total file system size number includes all mounted volumes. If the NTFS is mounted it counts.

---

### Post by sokekoke on 2010-08-31
When i unmount my NTSF i get, with "disk usage analyzer" capacity 32,3GB and total filesystem usage 24,7GB  = 7,6GB avaliable. When i get properties on filesystem it still says 5,9GB free.

The strangeness continues! :) where are you 1,7GB??

---

