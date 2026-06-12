---
title: "can't instal smbfs"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by madjack on 2007-11-12
I'm trying to mount a network drive, and to do this, I am trying to install smbfs, but it's failing. does anyone have any idea why ?

chris@work-laptop:~$ sudo apt-get install smbfs smbclient
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

---

### Post by elspiko on 2007-11-12
edit your /etc/apt/source.list file, make sure all the repositorys are enabled

---

### Post by madjack on 2007-11-12
> **elspiko said:**
> edit your /etc/apt/source.list file, make sure all the repositorys are enabled

chris@work-laptop:~$ cat /etc/apt/source.list
cat: /etc/apt/source.list: No such file or directory

what file are you talking about ?

---

