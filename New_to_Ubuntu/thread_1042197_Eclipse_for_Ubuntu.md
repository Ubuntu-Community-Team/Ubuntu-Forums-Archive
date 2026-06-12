---
title: "Eclipse for Ubuntu"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-17
Hi,

     I want to download eclipse for ubuntu. I went to the download site and they have two links for Linux. One is 32bit and other is 64bit. Which should I download? How can I find out which version I am using?

---

### Post by homemadejam on 2009-01-17
Hey,
You should be able to download it using:

```
sudo apt-get install eclipse
```

Jam

---

### Post by Nepherte on 2009-01-17
To answer the other part of your question: you can check your version with
```
uname -m
```
x86_64 is 64 bit, otherwise you're using 32bit (i386, i586, i686, x86 or whatever it is ubuntu will tell).

---

