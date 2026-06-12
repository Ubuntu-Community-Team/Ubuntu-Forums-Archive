---
title: "image backup software options"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Matt26 on 2009-01-09
does anyone know of any backup software for ubuntu which allows you to do all of the following tasks:

- create images of partitions or an entire hard disk
- restore individual files from a backup image
- set automated backup schedules

thanks for any suggestions.

---

### Post by nhasian on 2009-01-10
it doesnt backup parition images, but i like to use sbackup.

```
sudo apt-get install sbackup
```

its easy to schedule backups with it.

---

### Post by linuxford on 2009-01-10
I kind of like rsync, and I can synchronize folders from one hard-drive to another or from one computer to another.

After I mount my second drive, then I use this command.

```
$ rsync -avz /home/username/Downloads/ Downloads/
```

If I want to sychronize from a folder of one computer on my network to my local computer.

```
$ rsync -avz username@192.168.2.2:/home/username/Music/ Music/
```

---

### Post by Matt26 on 2009-01-10
> **nhasian said:**
> it doesnt backup parition images, but i like to use sbackup.

```
sudo apt-get install sbackup
```

its easy to schedule backups with it.

does sbackup allow for backups to be written to NTFS drives?  when i try to choose the destination for my backups my NTFS drives do not show up.

---

### Post by nhasian on 2009-01-10
is your ntfs drive mounted?  my DriveC isnt automounted, but i mounted it and then ran sbackup and it saw it as a destination directory.  

> **Matt26 said:**
> does sbackup allow for backups to be written to NTFS drives?  when i try to choose the destination for my backups my NTFS drives do not show up.

---

