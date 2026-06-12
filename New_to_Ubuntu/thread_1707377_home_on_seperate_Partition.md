---
title: "/home on seperate Partition"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Jonker on 2011-03-15
Hi,

I would like to put the /home folder of the users on a seperate partion. If possible on a FAT or NTFS partition.

---

### Post by Hippytaff on 2011-03-15
Your /home partition needs to be on an etc3 or 4 (linux) formatted partition. You can have a seperate ntfs /data partition that can be accessed by windows and linux, but not the /home folder - [this is worth a read]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

---

### Post by Jonker on 2011-03-16
how do I create new partitions, on the drive I'm working on (Gparted)? 
And how do I link it, so Ubuntu knows where to put the /home files?

---

### Post by Hippytaff on 2011-03-16
have a look at [this]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by beew on 2011-03-16
> **Hippytaff said:**
> have a look at [this]("http://www.psychocats.net/ubuntu/separatehome")

But be careful about this part

```
cd /old/home
find . -depth -print0 | cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
 
```Don't know what these do and the tutorial doesn't explain it. I tried the tutorial on my 10.04 system and ending up completely breaking it and had to do a clean install. Luckily that was an almost fresh install that I destroyed so it didn't take much work to reinstall it (I just wanted to try out the tutorial. Could have done a clean install to add the /home partition)

So be warned. :)

---

### Post by Objekt on 2011-03-16
Don't know of any way to do that on an existing install.  I always do it when installing Ubuntu, by choosing the option to manually set up partitions.

Another thing I do is choose a separate swap partition.  Ubuntu isn't addicted to disk swap space like Windows, but it's there if I ever need it.

If you want to be able to access users' /home folders from Windows, there are ways to do that.

---

### Post by Jonker on 2011-03-17
ok, the instruction worked fine. It is all working, but since I was Copy&Pasting the codes, I forgot once to change the device name... But I've repaired that misstake. Thanks!!!

---

### Post by Hippytaff on 2011-03-17
your welcome...remember to mark the thread as solved in the thread tools at the top of the page :-)

---

