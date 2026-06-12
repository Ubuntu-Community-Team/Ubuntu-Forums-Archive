---
title: "Cannot read software list"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Bob Denzel on 2009-08-23
Hi, 

Have been using system now for 2 months, suddenly cannot get updates!

error quoted when trying to use package manager is:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Can someone help please ???

Thanks

---

### Post by rsiddharth on 2009-08-23
Restart the computer and the Internet connection and try updating through command-line . 

commands to update the system through command-line :
```

sudo apt-get update 

```

```
 
sudo apt-get upgrade

```

This link may be of help to you : [http://ubuntuforums.org/showthread.php?t=94111](http://ubuntuforums.org/showthread.php?t=94111)

---

### Post by DougieFresh4U on 2009-08-23
In 'Applications>Accessories>Terminal
```
sudo apt-get -f install
sudo dpkg --configure -a
```
Try those 2 codes in terminal

---

### Post by Bob Denzel on 2009-08-24
> **rsiddharth said:**
> Restart the computer and the Internet connection and try updating through command-line . 

commands to update the system through command-line :
```

sudo apt-get update 

``````
 
sudo apt-get upgrade

```This link may be of help to you : [http://ubuntuforums.org/showthread.php?t=94111](http://ubuntuforums.org/showthread.php?t=94111)

Thanks for the prompt answer, am just trying it now :P

---

