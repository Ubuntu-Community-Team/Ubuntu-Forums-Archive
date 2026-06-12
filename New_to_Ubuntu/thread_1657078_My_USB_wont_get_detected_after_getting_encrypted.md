---
title: "My USB wont get detected after getting encrypted"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Mindswap1 on 2010-12-31
Hi guys! After I encrypted my USB Flash drive it stopped appearing in Ubuntu. How  can I bring it back? I was told that it would still work after encrypting by someone on the forums, but its not. What did I do wrong? Is it because its formated to FAT. Please help.

After typing in lsusb I got the following. 

```
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 154b:0048 PNY 
Bus 001 Device 004: ID 03f0:1f04 Hewlett-Packard 
Bus 001 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

the pny is the flash drive.

---

### Post by t4thfavor on 2010-12-31
How did you encrypt it, and with what? You will probably need to use whatever program you encrypted with, and the password you used to decrypt the filesystem so that it can be mounted. 

Encryption sometimes makes your dataz too secure, use with caution...

---

### Post by Mindswap1 on 2010-12-31
> **t4thfavor said:**
> How did you encrypt it, and with what? You will probably need to use whatever program you encrypted with, and the password you used to decrypt the filesystem so that it can be mounted. 

Encryption sometimes makes your dataz too secure, use with caution...


I encrypted with Trucrypt, but I don't know how to decrypt it with the program.

---

### Post by sandyd on 2010-12-31
> **Mindswap1 said:**
> I encrypted with Trucrypt, but I don't know how to decrypt it with the program.
Just click the "mount volume" button in truecrypt.

---

### Post by Mindswap1 on 2010-12-31
> **t4thfavor said:**
> How did you encrypt it, and with what? You will probably need to use whatever program you encrypted with, and the password you used to decrypt the filesystem so that it can be mounted. 

Encryption sometimes makes your dataz too secure, use with caution...

> **sandyd said:**
> Just click the "mount volume" button in truecrypt.

Thanks! That did the trick :) You truly rock!

Is there any other way to mount it?

---

### Post by sandyd on 2010-12-31
> **Mindswap1 said:**
> Thanks! That did the trick :) You truly rock!

Is there any other way to mount it?
nope.

---

### Post by muuwt1 on 2010-12-31
i dont really know but

mount -t vfat /dev/sdb1 /stick

works for my nonencypted stick

parted -l
or
fdisk -l 

will tell you where your stick is, for me usually /dev/sdb1
also gotta make sure /stick is an existing directory

---

### Post by Mindswap1 on 2010-12-31
How can I unencrypt it?

---

