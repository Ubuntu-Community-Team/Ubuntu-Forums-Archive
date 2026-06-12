---
title: "To many headers : Newbieee"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by pfwd.tech on 2007-06-03
I have noticed that i have many Linux headers in the /usr/src folder.  I have been trying to get my wireless usb adapter to work for the last 2 weeks with no luck.  Each time i have tried to do it it changes the headers.  
Should i delete them or are they needed?
This is a list of my usr/src folder:
ls
```
install_flash_player_9_linux.tar.gz  linux-headers-2.6.20-16-generic
linux-headers-2.6.20-15              rpm
linux-headers-2.6.20-15-generic      rt73-cvs-daily.tar.gz
linux-headers-2.6.20-16              rt73-cvs-daily.tar.gz
```
i dont know why the```
 linux-headers-2.6.20-15              rpm
```
is in there i thought rpm was for debian?

---

### Post by loathsome on 2007-06-03
No, RPM is more used in distros such as Red Hat Enterprise Linux, the Fedora Project, SUSE Linux Enterprise, openSUSE, CentOS, etc.

Debian and Ubuntu are pretty much the same; Ubuntu is built upon the Debian core :)

---

### Post by pfwd.tech on 2007-06-03
Oh ok so should i just leave these?

---

### Post by chili555 on 2007-06-03
These:> linux-headers-2.6.20-15                     rpmare two different things. If you do:```
 ls -al /usr/src
```you will see a list of directories, one of which is *linux-headers-2.6.20-15* and another of which is *rpm*. Why do you have a directory named *rpm*? Only you would know.

---

### Post by pfwd.tech on 2007-06-03
ic ok thanks

---

