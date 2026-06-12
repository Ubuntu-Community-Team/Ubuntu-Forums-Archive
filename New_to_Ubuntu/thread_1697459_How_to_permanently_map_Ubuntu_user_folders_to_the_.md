---
title: "How to permanently map Ubuntu user folders to the corresponding Windows user folders"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by HXM1 on 2011-02-28
I have a Dell desktop dual boot Windows XP Pro and Ubuntu.
The Hard drive is partitioned as follows:
1. The first primary partition is a small, about 300 MB or so for Dell’s diagnostics utilities.
2. The second is a primary partition, 12 GB, NTFS; this is where Windows is installed.
3. The third partition is an extended partition with multiple logical drives. All of the logical drives make up the Ubuntu installation except for the last logical drive is designated for data.    /   (250MB), /boot (1GB), /home (500MB), /tmp (2GB), /usr (3GB), /var (2GB), /swp (2GB), /SRV (1GB), /OPT (1GB) and /Store (NTFS 35GB) for documents.

In windows I’ve managed to move the Documents and Settings folder structure to the D:\ drive which is also the last logical drive (/Store). That is working fine in windows I was able to create new users w/o a problem.

Now I want to create the same users in Ubuntu, create the user folders in /home and permanently map them to the corresponding Windows user folders in  the Documents and Settings folder structure on the /Store (windows logical D:\ drive).

Please help.  I am new to Ubuntu. No technical Linux/Unix background.

---

### Post by blazemore on 2011-03-01
I have written a blog post about this here.
[http://blazemore.blogspot.com/2010/12/mirror-files-across-dual-boot.html](http://blazemore.blogspot.com/2010/12/mirror-files-across-dual-boot.html)

---

### Post by Mark Phelps on 2011-03-01
Windows and Linux use completely different permission schemes, so don't be surprised if, after you do this mapping, either Linux or Windows starts exhibiting problems.

And, BTW, if you hose up the Windows permissions messing with the files in Ubuntu, don't be surprised if Windows suddenly won't boot anymore.

---

### Post by Megaptera on 2011-03-01
This guide may be useful too:
"You can redirect the other commonly used folders like Documents, Downloads, Music, etc. to another partition, one that can be read by Windows."
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by matt_symes on 2011-03-01
Hi

I would keep your home folder on an extX partition and map other paritions for the linux / windows shared data using symbolic links to the correct partitions after mounting them in fstab. This is what i do.

Mark Phelps is right about the permissions. You can count ssh out and it could cause a whole host of other problems with permissions of configuration files.

EDIT: Seems i was beaten to it with that suggestion. There must be something in it then.

Kind regards

---

