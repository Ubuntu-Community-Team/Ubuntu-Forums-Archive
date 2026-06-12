---
title: "Folder Perrmission not changing on Mounted Drive"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by raziiq on 2009-06-26
Hi there.
I have a mounted Partition which is FAT formated. It contains my Documents, Pictures and Videos , so that i can access them from my Windows and Ubuntu. Now i want to lock one of my Folder on this drive in Ubuntu but the permissions are not changing on this folder. This is what i am doing.

```
sudo chmod -R 700 SomeFolder
```

When i use this command to see the permissions

```
ls -l
```

The persmissions are the same as they were before running the command for changing permission.

Am i doing something wrong?

---

### Post by pzs on 2009-06-26
FAT doesn't support permissions in this way.

[http://edge-op.org/grouch/fatperm.html](http://edge-op.org/grouch/fatperm.html)

---

### Post by HermanAB on 2009-06-26
Howdy,

Instead of FAT you should use NTFS or Ext3.  Linux supports NTFS and Windows supports Ext3 (with some minor effort).  

FAT corrupts easily, it has no journaling, no permissions and doesn't support large files.  So it is just bad news all around.

---

### Post by raziiq on 2009-06-27
Infact i have a triboot system, as u can see in my Signature, i have a Mac OS X also installed on my PC which doesnt support writing to NTFS (well it does using some apps), but i m much comfortable with FAT drives holding my Data.

---

### Post by raziiq on 2009-06-27
> **pzs said:**
> FAT doesn't support permissions in this way.

[http://edge-op.org/grouch/fatperm.html](http://edge-op.org/grouch/fatperm.html)

Thanks for the link man, i read it and got a bit of understanding of it too but the thing is using the unmask option, it will remove the write permissions from the whole Partition but what if i just want to remove the write permissions to just a single folder and not the others?

---

### Post by bodhi.zazen on 2009-06-27
> **raziiq said:**
> Thanks for the link man, i read it and got a bit of understanding of it too but the thing is using the unmask option, it will remove the write permissions from the whole Partition but what if i just want to remove the write permissions to just a single folder and not the others?

You can not do that with a FAT partition. You can set a dmask, but this applies to all directories, and you can set a fmask, and this applies to all files. 

The only way to be more selective is to use a file system that supports permissions.

---

### Post by raziiq on 2009-06-27
ok, means i need to put my data on NTFS partitions to be accessible from all 3 OS.

---

### Post by bodhi.zazen on 2009-06-27
NTFS does not support permissions either, lol

---

### Post by raziiq on 2009-06-27
ohhhhh, then what should i go for. I mean with this triboot what should i do? Any good suggestions?

---

### Post by kixome on 2009-06-27
ntfs does support permissions, and yes your files should reside on an ntfs or ext3 partition

---

### Post by kixome on 2009-06-27
Windows xp home and i think vista home don't support permissions, I think this is what that guy was talking about.

---

### Post by bodhi.zazen on 2009-06-27
Well you will have to make some kind of compromise.

I suggest FAT as it is probably easiest.

ext2 is not bad either, you can mount ext2 in windows, although again I do not believe the windows drier supports permissions (even if the file system is ext2/3).

---

### Post by kixome on 2009-06-27
If mac supports reading from an ext3 partition, then use that and install [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) for windows, and you should be able to read linux partitions

---

