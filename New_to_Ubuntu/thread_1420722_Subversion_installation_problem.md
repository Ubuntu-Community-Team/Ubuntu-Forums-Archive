---
title: "Subversion installation problem"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by navaneethan on 2010-03-03
i need to install subversion in my hardy but i unable to do it
it shows the error when i hit "apt-get install subversion"

any solution??

> root@navtux-desktop:~# apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  db4.6-util subversion-tools
The following NEW packages will be installed:
  subversion
0 upgraded, 1 newly installed, 0 to remove and 58 not upgraded.
Need to get 243kB of archives.
After this operation, 3482kB of additional disk space will be used.
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main subversion 1.4.6dfsg1-2ubuntu1.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main subversion 1.4.6dfsg1-2ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.4.6dfsg1-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.4.6dfsg1-2ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@navtux-desktop:~# 



---

### Post by gmargo on 2010-03-03
> 
Could not resolve 'in.archive.ubuntu.com'
Could not resolve 'security.ubuntu.com'
Fix your DNS problem first.

---

### Post by navaneethan on 2010-03-04
> **gmargo said:**
> Fix your DNS problem first.
Please i am a newbie can you give suggestion how to fix the DNS problem?

---

### Post by realzippy on 2010-03-04
run in terminal:

**sudo apt-get update**

first

---

