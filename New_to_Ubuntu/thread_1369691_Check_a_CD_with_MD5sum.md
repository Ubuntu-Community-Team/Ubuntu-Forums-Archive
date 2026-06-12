---
title: "Check a CD with MD5sum ?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by L Campbell on 2010-01-01
I have a CD with 8.04.3 on it that I would like to check with MD5sum.

It shows up on my Desktop as Ubuntu 8.04.3 i386 so I tried this in terminal:-

qwer@qwer-desktop:~$ md5sum Ubuntu 8.04.3 i386

md5sum: Ubuntu: No such file or directory
md5sum: 8.04.3: No such file or directory
md5sum: i386: No such file or directory

I would appreciate it if you could tell me what I 'should' have done.

TIA

---

### Post by Temposs on 2010-01-01
Do this:

```
md5sum /dev/cdrom
```

Depending on what your system is doing, you may have to change it to "cdrom0" or "cdrom1".

---

### Post by L Campbell on 2010-01-01
> **Temposs said:**
> Do this:

```
md5sum /dev/cdrom
```

Depending on what your system is doing, you may have to change it to "cdrom0" or "cdrom1".

Thanks very much, that worked perfectly.

Kind regards.

---

### Post by candtalan on 2010-01-01
Glad that you found it worked.

I have two CD drives in a PC and it is not easy to remember exactly what each is seen as.

I have found a useful method is to insert a cd into one drive, wait a few moments until it is automatically mounted - and shown on the desktop - then open a terminal and  type
mount
the resulting screen full of information includes the mounted CD, for my case this is typically
/dev/scd0  or maybe /dev/scd1

hth

---

### Post by Sef on 2010-01-01
> I have a CD with 8.04.3 on it that I would like to check with MD5sum.

It shows up on my Desktop as Ubuntu 8.04.3 i386 so I tried this in terminal:-

qwer@qwer-desktop:~$ md5sum Ubuntu 8.04.3 i386

md5sum: Ubuntu: No such file or directory
md5sum: 8.04.3: No such file or directory
md5sum: i386: No such file or directory

I would appreciate it if you could tell me what I 'should' have done.


You need to type it like this for the 9.10 32-bit desktop:

```
md5sum ubuntu-9.10-desktop-i286.iso
```

---

