---
title: "Using Ubuntu for Data Recovery"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by sugarashii on 2009-08-20
Hello everyone,

I'm not sure if this is the right place to post this, but as I'm relatively new to Ubuntu, I figured this would be a good place to start.

A few weeks ago I was having problems trying to access one of my Windows partition.  So I decided to try to recover it using my still working Ubuntu partition.  I followed the guides from these links:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)

using GNU ddrescue to try to recover what I could from my disk.

It seems to work ok until I get to the section where the forensics wiki tells me to change to raw device access.  Here is what I get from the terminal:

```
root@sugar-linux:~# modprobe raw
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
root@sugar-linux:~# raw /dev/raw/raw5 /dev/sda5
Cannot locate raw device '/dev/raw/raw5' (No such file or directory)
```Does anyone know what is wrong here?  Any help would be appreciated :)

---

### Post by jerrrys on 2009-08-20
if you cant get an answer, you may want to try this

[http://ubuntuforums.org/showthread.php?p=7816242#post7816242](http://ubuntuforums.org/showthread.php?p=7816242#post7816242)

---

