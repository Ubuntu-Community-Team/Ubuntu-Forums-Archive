---
title: "Ubuntu-USB setup"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Don1500 on 2009-11-19
I set up Ubuntu (9.10) on a 8 gig USB pen drive.
It works fine, I'm using it now on my Dell D620 Laptop. 
I have flash and wireless installed and running so that part is fine.
The problem is that the /home directory only shows 4 meg left on the drive.
When I run G-Parted it shows the over 6 gig available but properties on the File System shows 0 space left.
and the Disk usage Analyzer shows 100% used on the / folder.

How can I get Ubuntu to recognize the complete drive?

---

### Post by balachandarlinks on 2009-11-19
> **Don1500 said:**
> I set up Ubuntu (9.10) on a 8 gig USB pen drive.
It works fine, I'm using it now on my Dell D620 Laptop. 
I have flash and wireless installed and running so that part is fine.
The problem is that the /home directory only shows 4 meg left on the drive.
When I run G-Parted it shows the over 6 gig available but properties on the File System shows 0 space left.
and the Disk usage Analyzer shows 100% used on the / folder.

How can I get Ubuntu to recognize the complete drive?
Hi Don150,
   Use "cd /" to go under your root and then try to use this command with root user privilege. "du -hsc *"
   It ll clearly tell you the size of your every directory.Then By analyzing that you can get some help.

---

### Post by Don1500 on 2009-11-19
> **balachandarlinks said:**
> Hi Don150,
   Use "cd /" to go under your root and then try to use this command with root user privilege. "du -hsc *"
   It ll clearly tell you the size of your every directory.Then By analyzing that you can get some help.

output of du -hsc *
```
5.3M	bin
11M	boot
826M	cdrom
648K	dev
7.9M	etc
du: cannot access `home/ubuntu/.gvfs': Permission denied
38M	home
0	initrd.img
108M	lib
12K	lost+found
27G	media
0	mnt
0	opt
du: cannot access `proc/14141/task/14141/fd/4': No such file or directory
du: cannot access `proc/14141/task/14141/fdinfo/4': No such file or directory
du: cannot access `proc/14141/fd/4': No such file or directory
du: cannot access `proc/14141/fdinfo/4': No such file or directory
0	proc
1.8G	rofs
121K	root
9.6M	sbin
0	selinux
0	srv
0	sys
12K	tmp
1.6G	usr
107M	var
0	vmlinuz
31G	total

```

---

### Post by Don1500 on 2009-11-19
bump

---

### Post by Don1500 on 2009-11-20
pmub

---

### Post by Mighty_Joe on 2009-11-20
Did you do a full install or did you use the Live USB Creator?  If you used the Live USB creator, the free space available will be equal to the amount of space you selected for the "persistent partition", not the free space available on the drive.

---

### Post by Don1500 on 2009-11-29
> **Mighty_Joe said:**
> Did you do a full install or did you use the Live USB Creator?  If you used the Live USB creator, the free space available will be equal to the amount of space you selected for the "persistent partition", not the free space available on the drive.

Doh! Yep, that was it.

---

