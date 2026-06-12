---
title: "Problen sharing files and folders"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by mikro 402 on 2011-04-09
When I try to set up a share I get this error: Failed to execute child process "testparm" (No such file or directory)

I was trying to figure out if I have samba installed.

I have Ubuntu 10.10.

---

### Post by Morbius1 on 2011-04-09
See if you have the following package installed:
```
sudo apt-get install samba-common-bin
```

---

### Post by mikro 402 on 2011-04-09
> **Morbius1 said:**
> See if you have the following package installed:
```
sudo apt-get install samba-common-bin
```

Here is the output :

den@ubuntu:~$ sudo apt-get install samba-common-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
den@ubuntu:~$ 


Mikro

---

### Post by mikro 402 on 2011-04-09
That output I posted was from the wrong machine. I ran the command from the machine that gave me the error and the package was not installed. It's ok now.

Thank you ,

Mikro

---

