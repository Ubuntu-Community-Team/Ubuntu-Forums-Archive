---
title: "How to get more information on partitions and &quot;files&quot; on /dev"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Geraba on 2009-12-03
I was wondering how can I get more info on those "files" on /dev using the command line (not Disk Utility). If ever get stuck with the command line, how would I know which one is my USB Drive, each partition size, format etc...
Also, what those files in /dev called, character/block special?

---

### Post by whitethorn on 2009-12-03
Two commands I find really useful are.

```
df -h
```
```
sudo fdisk -l
```

If you only want to see the partitions on a specific harddrive in /dev

then example:

```
sudo fdisk -l /dev/sda1
```

---

### Post by oldos2er on 2009-12-03
[http://linux.about.com/od/lsa_guide/a/gdelsa18.htm](http://linux.about.com/od/lsa_guide/a/gdelsa18.htm)

---

### Post by Geraba on 2009-12-04
Thanks whitethorn and oldos2er!! That's exactly what I meant...
Great info!!

---

### Post by Paqman on 2009-12-04
The main thing to understand is that in Linux, everything is a file. So you'll get devices that are represented as files in /dev.

---

