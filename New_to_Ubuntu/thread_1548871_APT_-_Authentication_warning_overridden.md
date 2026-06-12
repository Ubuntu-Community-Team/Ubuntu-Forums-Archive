---
title: "APT - Authentication warning overridden"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by yaami on 2010-08-09
Hi all,

I believe Mint and Ubuntu are almost the same. And hence I'm asking this question here. I use Mint 9. 

The problem is that when I use apt to install packages it gives me this warning: **WARNING: The following packages cannot be authenticated!** always. Here is a sample.

```
$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
linux-image-2.6.32-24-generic
The following packages will be upgraded:
linux-generic linux-headers-generic linux-image-generic
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.1MB of archives.
After this operation, 184MB of additional disk space will be used.
Do you want to continue [Y/n]? y
**WARNING: The following packages cannot be authenticated!**
linux-image-2.6.32-24-generic linux-generic linux-image-generic
linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
linux-headers-generic
**Authentication warning overridden**.
```


I did apt-key update, but the problem still lasts. How to get rid of this annoying warning. I've used ubuntu and also debian for a while now. I just wanted to try mint as-well. Never had issues like this before and also never paid attention to package management. Any suggestions which will help me get rid of this...

Thanks.

---

