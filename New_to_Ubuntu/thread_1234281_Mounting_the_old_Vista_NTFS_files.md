---
title: "Mounting the old Vista NTFS files"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by jqke on 2009-08-07
Just switched to Ubuntu from Vista 64b bit and I'm attempting to gain access to my files from windows.

I found the code on ubuntu dapper:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

But my windows files are not located at /dev/hdal

How do I find out what to put instead of /dev/hdal?


Thanks in advance for you help.

---

### Post by jqke on 2009-08-07
It tells me

mount:special device /dev/hdal does not exist

---

### Post by Liolikas on 2009-08-07
sudo fdisk -l

---

### Post by Buuntu on 2009-08-07
It's much easier to just double click on the partition you want to use in Computer.  
Similarly you can right click on the partition and select "Mount". 

Either of those should automatically mount it as /media/disk#.

---

