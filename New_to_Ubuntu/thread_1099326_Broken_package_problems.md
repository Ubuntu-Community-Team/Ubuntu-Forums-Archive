---
title: "Broken package problems"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by AncientPC on 2009-03-18
When installing a package (hugs) through apt-get my laptop had a kernel panic and I had to do a hard reset. Upon starting up, I ran fsck all the partitions (jfs) and rebooted into Ubuntu.

However hugs was unconfigured and can't be installed / removed. I tried an apt-get purge and dpkg --configure -a / dpkg --remove -f hugs but the error message in all cases is:

```
root@core:/var/lib/aptitude# dpkg --remove hugs
(Reading database ... 161721 files and directories currently installed.)
Removing hugs ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing hugs (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hugs

root@core:~# aptitude install -f hugs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  hugs 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up hugs (98.200609.21-5) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing hugs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hugs
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

---

### Post by AncientPC on 2009-03-23
bump, can anyone provide any insight?

---

### Post by Xiong Chiamiov on 2009-03-23
I'm not familiar enough with apt to give any solid advice, but I'd take a read through [this](http://www.mail-archive.com/debian-user@lists.debian.org/msg81730.html) and [this](http://tumblr.alancfrancis.com/post/22544036/ok-when-you-see-unable-to-execute) and see if you can apply any principles from either of those to this problem.

---

### Post by hyper_ch on 2009-03-23
I'd say you'll have to force install/remove the hugs package with "dpkg"

---

