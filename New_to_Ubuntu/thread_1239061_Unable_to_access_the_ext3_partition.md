---
title: "Unable to access the ext3 partition"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by lgjsheron on 2009-08-13
I'm new to Ubuntu n i'm using Ubuntu 9.04, and i remove Windows XP and put Ubuntu in a single boot. After that i try to change the NTFS partition to ext3. And it sucessfully change it using GParted, but now i have a problem to acess the drive. It open but unable to create or copy a file into that directory. When i check the Permission tab it shows Permission not define. What i want to do .

---

### Post by plucky on 2009-08-13
> **lgjsheron said:**
> I'm new to Ubuntu n i'm using Ubuntu 9.04, and i remove Windows XP and put Ubuntu in a single boot. After that i try to change the NTFS partition to ext3. And it sucessfully change it using GParted, but now i have a problem to acess the drive. It open but unable to create or copy a file into that directory. When i check the Permission tab it shows Permission not define. What i want to do .

Read this link [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Good Luck

---

### Post by django0909 on 2009-08-13
As far as I'm aware, you can't make alterations to a drive that is already mounted. Have you tried downloading a GParted live CD and booting into that? It should give you access to all parts of the drive.

---

### Post by superprash2003 on 2009-08-13
in your terminal type** sudo nautilus** and then browse to the ext3 partition and then try copying files etc..

---

