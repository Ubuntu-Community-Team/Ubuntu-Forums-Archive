---
title: "ubuntu-8.10-desktop-i386"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by joe2005 on 2009-04-08
I am very new to linux and to this forum.I have installed Ubuntu 8.10 in Windows XP using WUBI and I am slowly coming to terms with this OS.Being used to Windows for a long time it is bit difficult to adjust.My first newbie question is:How do I see all partitions?At present I am able to see D E F but not C .I hope I have made myself clear.Thanks

---

### Post by kpkeerthi on 2009-04-08
Linux uses a different convention to name/identify your hard disk partitions. This guide might help you understand a bit more. [http://www.linuxplanet.com/linuxplanet/tutorials/4269/3/](http://www.linuxplanet.com/linuxplanet/tutorials/4269/3/)

To see all your partition, open a terminal and type
```
sudo fdisk -l
```

---

### Post by MrWES on 2009-04-08
> **joe2005 said:**
> I am very new to linux and to this forum.I have installed Ubuntu 8.10 in Windows XP using WUBI and I am slowly coming to terms with this OS.Being used to Windows for a long time it is bit difficult to adjust.My first newbie question is:How do I see all partitions?At present I am able to see D E F but not C .I hope I have made myself clear.Thanks

I believe under Wubi the C:\ drive is located at /host.

Bill

---

### Post by joe2005 on 2009-04-09
Thanks kpkeerthi for the guide
Thanks MrWES.Yes c drive is called host.My doubt cleared.
May be coming back with some more doubts in due course.thanks

---

