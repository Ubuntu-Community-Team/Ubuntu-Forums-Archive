---
title: "Error installing applications"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by paulvic on 2010-04-12
Help!  I can't install or update applications any longer.  I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I do now?

Thanks,

Paul Terhorst

---

### Post by e4uforums on 2010-04-12
did you run

```
dpkg --configure -a
```

or 

```
sudo dpkg --configure -a
```

?

---

### Post by sisco311 on 2010-04-12
Open a terminal (Applications -> Accessories -> Terminal)
and run:
```
sudo dpkg --configure -a
```

---

### Post by paulvic on 2010-04-12
> **sisco311 said:**
> Open a terminal (Applications -> Accessories -> Terminal)
and run:
```
sudo dpkg --configure -a
```

Thanks, that worked!  But now I have a "Broken" file.  I try to remove and get the following error message: E: cli-common: cannot remove `/.'

Also when I open Add/Remove applications a message says I have a "major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

How do I check the correctness of '/etc/apt/sources.list' ?  When I put this file in terminal I get a message "permission denied."

Thanks,

Paul

---

### Post by sisco311 on 2010-04-12
Please post the output of:
```
ls -al /etc/apt/sources.list
```
and
```
sudo cat /etc/apt/sources.list
```

---

### Post by paulvic on 2010-04-12
> **sisco311 said:**
> Please post the output of:
```
ls -al /etc/apt/sources.list
```
and
```
sudo cat /etc/apt/sources.list
```

On the first I get:

rw-r--r-- 1 root root 1034 2009-03-19 01:23 /etc/apt/sources.list

On the second I get:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted



Thanks again!

Paul

---

