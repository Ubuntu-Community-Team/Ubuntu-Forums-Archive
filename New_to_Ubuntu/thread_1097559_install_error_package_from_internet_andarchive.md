---
title: "install error package from internet andarchive"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by hoangtukan on 2009-03-16
I'm a newbie but i like Ubuntu very much.it's the first time i use it.
 After then,it's error I see in gnome-terminal:( for example):
 "" . dpkg: error process /var/cache/apt/archives/exim4-config_4.69-2_all.deb (--unpack):
    files list file for package `d4x-common' is missing final newline
   A error process:
   /var/cache/apt/archives/exim4-config_4.69-2_all.deb
   procees stops because of many errors.
  E: Sub-process /usr/bin/dpkg returned an error code (1)""
And i can't install any more software. any software from internet and local computer.
when i install software it also error "d4x-common" is missing final newline" and process stop.
                    Help me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!.Thank you very much

---

### Post by billgoldberg on 2009-03-16
> **hoangtukan said:**
> I'm a newbie but i like Ubuntu very much.it's the first time i use it.
 After then,it's error I see in gnome-terminal:( for example):
 "" . dpkg: error process /var/cache/apt/archives/exim4-config_4.69-2_all.deb (--unpack):
    files list file for package `d4x-common' is missing final newline
   A error process:
   /var/cache/apt/archives/exim4-config_4.69-2_all.deb
   procees stops because of many errors.
  E: Sub-process /usr/bin/dpkg returned an error code (1)""
And i can't install any more software. any software from internet and local computer.
when i install software it also error "d4x-common" is missing final newline" and process stop.
                    Help me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!.Thank you very much

Open a terminal and enter this command

```
sudo apt-get update
```

Copy paste the error it gives here.

---

### Post by hoangtukan on 2009-03-17
Can't fix it. Do you have other way?
 /// 
 dpkg: parse error, in file `/var/lib/dpkg/available' near line 1189 package `openoffice.org':
 field name `1' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
////
 or
 
/////
dpkg-query: parse error, in file `/var/lib/dpkg/available' near line 1189 package `openoffice.org':
 field name `1' must be followed by colon
exim4-config.postinst: [WARN] Installed debconf version is broken. Aborting preconfigure.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1189 package `openoffice.org':
 field name `1' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
////
 and don't install nay more software.
  Thank you

---

