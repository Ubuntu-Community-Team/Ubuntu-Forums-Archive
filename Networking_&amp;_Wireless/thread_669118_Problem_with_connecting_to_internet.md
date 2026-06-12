---
title: "Problem with connecting to internet"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by BlackFoxTR on 2008-01-16
Hi
I just installed Ubuntu 7.10. My problem is I 'm able to connect to network but not to internet. I have Atheros Ethernet card(also bought realtek ethernet). I were using ubuntu 7.04 and everything were ok. Even after update to 7.10. But after i installed 7.10 from cd i got this problem.

Sorry for my english.
Regards

---

### Post by sdide on 2008-01-16
Can you 
1:
$ ping 66.102.9.99
2:
$ ping [www.google.com](www.google.com)

if 1 and not 2, you are missing your nameservers
please post output of 
$ cat /etc/resolv.conf

---

### Post by BlackFoxTR on 2008-01-16
It's done. i ping to both. but internet is so slow.

---

### Post by BlackFoxTR on 2008-01-16
Now i have an another problem

```
root@fox-desktop:/home/fox# sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-tr
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-tr
30% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting t30% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
```

---

