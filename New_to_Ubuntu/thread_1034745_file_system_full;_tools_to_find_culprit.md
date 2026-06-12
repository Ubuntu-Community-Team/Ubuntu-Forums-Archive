---
title: "file system full; tools to find culprit?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by ThunderRd on 2009-01-09
I have finally figured out how to build a kernel for my machine and had a few failed attempts before succeeding.

I notice now that my system drive is showing it is at 100% in the disk usage analyzer, but I can't imagine how it could be.  I found this out because I attempted to untar a 50MB file and could not, with an error message that there was no more space.

This was a clean installation of 8.10 before the kernel building experiments, so I'm sure that there are remnants of the failed attempts on the drive somewhere but I can't find them.  How can I get some better answers about specifically what has filled up the drive, and where?  Disk usage analyzer isn't exactly clear.

---

### Post by jamin_melville on 2009-01-09
Disk Usage Analyzer is probably the best option, you just have to scan filesystem and it will show you what size and where all your files and folders are.

---

### Post by handydan918 on 2009-01-09
Silly question:
Empty the trash?

---

### Post by iaculallad on 2009-01-09
Try cleaning up your Kernel source directory:

```
make-kpkg clean
```

---

### Post by kaibob on 2009-01-09
The following entered in a terminal window will show all files in excess of 10 MB in the current partition:

```
sudo find / -xdev -size +10M -type f -exec ls -gohX {} \;
```

---

### Post by Paqman on 2009-01-09
> **jamin_melville said:**
> Disk Usage Analyzer is probably the best option

Indeed it is. One trick to using it is that it can be handy to run it as root if you can't find the offending files. To run it as root use:
```
gksu baobab
```

(Since the disk usage analyser that Ubuntu includes is actually called Baobab)

---

### Post by ThunderRd on 2009-01-09
> **Paqman said:**
> Indeed it is. One trick to using it is that it can be handy to run it as root if you can't find the offending files. To run it as root use:
```
gksu baobab
```

(Since the disk usage analyser that Ubuntu includes is actually called Baobab)

Thanks to all for the suggestions, I'll try them out later today.

As for Disk Usage Analyzer, what I can't get my head around is this.  I have a 15G partition for the OS, with /home on a seperate partition.  DUA shows / at 100%; but the total of all the directories under / [/usr, /var, etc.] don't add up to that figure.  I'm probably not reading it correctly or something.  I have to study it a bit more.  I also see that if another physical hard drive is mounted in /mnt, for example, DUA sees this as data to report, even though the data are on another physical drive.  So that is a bit confusing, too.

---

### Post by computermacgyver on 2009-01-09
Yes, that does seem a bit strange:
```
df -h
```
will show all the partitions / mount points and their free/used space.

---

