---
title: "How to create an image of an external hdd"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Haur on 2011-08-04
Good day.

I've got this external hdd that contains some backup data from mac laptop. I need to reformat the drive but also take a backup of the data it contains. I've tried just plain of copying the data over the my hard drive but can't because of some permission problems. So i thought that maybe creating a hard drive image would solve my problem. Then afterwards i could just burn the image to a sepparte hdd. My main problem is i can't seem to find a easy enough program to do these tasks.

I gather i could use Clonezilla to do it, but that would mean creating a live cd and i'm all out of cd's. Surly there is a easier way?

---

### Post by Beacon11 on 2011-08-04
You can use dd, which is already on Linux.

To create an image:
```
dd if=/dev/sda of=mydisk.img
```

To clone the image onto another disk:
```
dd if=mydisk.img of=/dev/sdb
```

/dev/sda and /dev/sdb are examples; make sure you know what yours are before you run these commands. Also, be careful that the destination hard drive is not smaller than the source hard drive, or dd won't be able to put the whole image on it and it may result in corrupted data. Also note that this process will take quite some time and dd does not give a progress indicator. The only way to view its progress is by sending it the USR1 signal (e.g. kill -USR1 <dd pid>). My method of choice is normally dd in combination with kill and the watch command.

---

### Post by Haur on 2011-08-12
Using the first command gives me an empty image file. This is the output i get.
```
kristjan@Dune-Arakis:~$ dd if=/media/Extdata/ of=macbackup.img
dd: reading `/media/Extdata/': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000302059 s, 0.0 kB/s

```

---

### Post by Beacon11 on 2011-08-12
Ah shoot, I'm sorry, I wasn't thinking properly. You need the device path, not the mount point. Please see the updated post above.

---

### Post by Haur on 2011-08-12
No problem. One thing before i go through with it though. The space requirement i need on my internal hdd only has to be greater then the data on the external partition that i want to backup, not the size of the entire partition itself right?

---

### Post by Rhizoid on 2011-08-12
I'm not sure DD is the right tool for the job here as it will copy not just the data but the partition information too, so when you restore it you'll be back to a mac partition.

What are the permissions errors/problems you're having and how are they manifest by the OS?

You could try this:

```
sudo tar -cvzf ~/backup.file.tar.gz /mount/point
```Using 'sudo' should overcome any rights issues, the 'tar -cvzf' creates a compressed archive of the files in '/mount/point' to a file in your home folder called 'backup.file.tar.gz'  You will definitely need only the space currently used by the files you're backing up to store 'backup.file.tar.gz' in your home folder.

To uncompress the image file you create, copy it to the directory you wish to put the data in and use this command in terminal:

```
tar -xvz backup.file.tar.gz
```Let us know if that does or doesn't help,

Cheese!

---

