---
title: "Checksum"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-04-02
Can someone point me to a page/thread that will explain how to use a checksum?

I use it to verify my binary software packages, but have never used it with Ubuntu software.  

Thanks,
MarkN

---

### Post by PCNetSpec on 2011-04-02
To generate an MD5 checksum (hash), open a terminal and enter:

**md5sum /path/to/file/filename**

Hit enter and you will get a single line output like:

**59d15a16ce90c8ee97fa7c211b7673a8**  /home/mark/Desktop/Distros/ubuntu-10.10-desktop-i386.iso

also see here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

SHA-1 hash's can be generated with:

**sha1sum /path/to/file/filename**

there are also SHA-2 hash generators -

sha224sum
sha256sum
sha384sum
sha512sum

hth.

---

