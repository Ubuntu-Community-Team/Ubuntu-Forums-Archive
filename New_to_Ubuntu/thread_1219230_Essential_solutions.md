---
title: "Essential solutions"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by navaneethan on 2009-07-21
Hi all,

 problems
         
         1. Monitor flickering in ubuntu,
           
                         Is any solution to install video driver which makes good


         2.Unclean shut down

                          I have shutdown improper manner,so i can't able to access windows drives,i have tried that editing fstab,using mount command     but it is not working



          Can you able to give any suggestion to me??

---

### Post by saj0577 on 2009-07-21
When you say you cant access windows driver you cant boot them or you cant access them?

Saj

---

### Post by navaneethan on 2009-07-22
> **saj0577 said:**
> When you say you cant access windows driver you cant boot them or you cant access them?

Saj


when incomplete shutdown occrs in windows means i can't able to access windows drive in ubuntu

any solution?

---

### Post by cariboo on 2009-07-22
Shutdown Windows properly is the best way to keep your ntfs drives clean. you can try a force mount with a command like this:

```
mount -t ntfs-3g /dev/sdc1 /media/external/ -o force
```

I wouldn't advise using the force option as you may end up losing some data.

---

