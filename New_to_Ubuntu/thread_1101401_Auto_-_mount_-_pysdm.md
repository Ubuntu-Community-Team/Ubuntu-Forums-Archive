---
title: "Auto - mount - pysdm"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by cool-linux on 2009-03-20
Hello,

im new in ubuntu and linux

i download from here [http://ubuntudoitall.blogspot.com/2009/01/easy-auto-mount-any-partition.html](http://ubuntudoitall.blogspot.com/2009/01/easy-auto-mount-any-partition.html)

its a little programm called pysdm

i run it in terminal and when i mount my second hd i take error

mount error 13 = Permission denied

my brothers pc works like a charm...

i have interpid 8.10

any help?

Thanks

---

### Post by mhh91 on 2009-03-20
> **cool-linux said:**
> Hello,

im new in ubuntu and linux

i download from here [http://ubuntudoitall.blogspot.com/2009/01/easy-auto-mount-any-partition.html](http://ubuntudoitall.blogspot.com/2009/01/easy-auto-mount-any-partition.html)

its a little programm called pysdm

i run it in terminal and when i mount my second hd i take error

mount error 13 = Permission denied

my brothers pc works like a charm...

i have interpid 8.10

any help?

Thanks

maybe you have to mount it as root

by the way,pysdm is in the repositories already,you'll find it in synaptic :)

---

### Post by coolworm on 2009-03-20
ok , i didnt know... sorry , i just search on google for auto mount.

sudo didnt work.

:( still searching

---

### Post by vanadium on 2009-03-20
We could troubleshoot manually if you copy/paste the output here of following commands, run in the terminal:

```

mount
cat /etc/fstab
sudo fdisk -l
sudo blkid

```

(You will need to supply your login password for the first sudo command. While typing it, you see nothing - this is normal).

---

