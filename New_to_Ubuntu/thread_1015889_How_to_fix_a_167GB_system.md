---
title: "How to fix a 167GB system"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-12-19
Hi
I tried to backup my entire system, using "Simple Backup".   
It used 100% cpu time for a good one hour, and somehow created a huge file(s) occupying up to 160GB - 86% of the disk, as shown below.  

The output of "df -h"

Filesystem  Size  Used  Avail  Use% Mounted on
/dev/sda5   206G  167G  28G    86%  /
tmpfs       1.7G  0     1.7G   0%   /lib/init/rw
varrun      1.7G  316K  1.7G   1%   /var/run
varlock     1.7G  0     1.7G   0%   /var/lock
udev        1.7G  2.8M  1.7G   1%   /dev
tmpfs       1.7G  12K   1.7G   1%   /dev/shm
lrm         1.7G  2.0M  1.7G   1%   /lib/modules/2.6.27-9-generic/volatile

My system is Ubuntu 8.10 in which "mountdevsubfs.sh" and "fstab" are modified for USB use in VirtualBox in addition to replacement of 40-permissions.rules and 60-persistent-storage.rules for an external USB HD.

I could not locate this huge troubling file(s).  Any help is appreciated and thanks in advance.

---

### Post by Paqman on 2008-12-19
> **flutti-tutti said:**
> 
I could not locate this huge troubling file(s).  Any help is appreciated and thanks in advance.

Try running the disk usage analyser as root:
```
gksu baobab
```

---

### Post by flutti-tutti on 2008-12-19
thanks for your reply.
I run "gksu baobab" and found out that "var/backup/" contained huge backup files, causing the problem.  So, I removed the package "Simple Backup", and "gksu nautilus" to eliminate the troubling files, "Move to Trash".    The files were moved /.local/share/Trash. I could not erase them. somehow, some files kept growing and a free space quickly disappeared, while I was doing it.  Now I could not get into Ubuntu, citing no free space on HD.  Please advise on how to get in Ubuntu and get rid of /.local/share/Trash.  My system is configured as a dual boot system with Vista and Ubuntu.  Thanks

---

### Post by Titan8990 on 2008-12-19
Are you sure it wasn't in ~/.local/share/trash or /root/.local/share/trash and not /.local/share/trash?

---

### Post by Paqman on 2008-12-19
If you boot into recovery mode and drop to the command line you'll be able to delete anything you want. However, be careful. When deleting files as root from the command line, you should double and triple check before you delete.

To delete a folder from the command line as root:
```
rm -rf /path/to/folder
```

---

### Post by Titan8990 on 2008-12-19
When you follow Paqman's suggestion, make sure that the path you are deleting is correct because the rm -rf command as root can cause irreversible damage if used on the wrong directory.

---

### Post by flutti-tutti on 2008-12-19
After booting into recovery mode and dropping to the command line,

I run 
root@k32:/#  rm -rf /root/.local/share/trash
and the files were not removed.  
"df -h" indicated 100% usage of HD,

With -ri option, I got a message "no such file or directory".

What is wrong with the above command? 
(is there any command to see such directories as ".local"?)

---

### Post by louieb on 2008-12-19
> **flutti-tutti said:**
> 
(is there any command to see such directories as ".local"?)
```
ls -a
```
or```
ls -la
```

---

### Post by flutti-tutti on 2008-12-19
Thanks for your prompt responses.
I am finally able to remove the problem files and log in Ubuntu.
I appreciate your help.

---

