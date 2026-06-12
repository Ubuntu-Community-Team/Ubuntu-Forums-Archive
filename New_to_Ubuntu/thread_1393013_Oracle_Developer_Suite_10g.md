---
title: "Oracle Developer Suite 10g"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by mevets on 2010-01-28
Im trying to install Oracles 10g Developer Suite for a database class im taking. I know 11g is out but they want us to use 10g. I downloaded both parts at [http://www.oracle.com/technology/software/products/ids/htdocs/101202linuxsoft.html](http://www.oracle.com/technology/software/products/ids/htdocs/101202linuxsoft.html) . I 'cksum'ed both parts so I know the files are not corrupted.

Oracles page says you must "To extract the cpio file, move the cpio file to an empty directory, then do: cat filename.cpio | cpio -icd". I did just that on disk 1 and it tells me there is a premature end to the file

```
steve@steve-desktop:~/Desktop/disk1$ cat as_linux_x86_ids_101202_disk1.cpio | cpio -icd
cpio: premature end of file

```
Does anyone know how to fix this problem and know another way to install oracles developer suite 10g?

---

### Post by silverag47 on 2010-02-01
Try running it without the "c"

cpio -id

That worked for me

---

### Post by hendra40 on 2010-02-23
I have the other way :
terminal : cat as_linux_x86_ids_101202_disk2.cpio | cpio -idmv

but after I extract it.
I change directory with :
terminal : cd Disk1

After that with :
terminal : bash runInstaller

The output is :
Checking operating system version: must be redhat-2.1, redhat-3, redhat-4, SuSE-8, SuSE-9 or UnitedLinux-1.0


So, the conclusion is oracle developer suite 10g can not be installed on ubuntu.

---

