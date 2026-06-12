---
title: "error in terminal"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by hatridge on 2010-04-07
Hi...No matter what I do in my terminal I am getting errors. I used restricted extras for an example. Please help as it is limiting my ability to install software....

jim@jim-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-evolution (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gtkmozembed (2.25.3-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gtkmozembed (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-wnck (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-evolution
 python-gtkmozembed

---

### Post by Didius Falco on 2010-04-07
Try running this command:

```
sudo dpkg --configure -a
```

That tells dpkg to try to fix the broken packages.

Post back with the results.

Regards,

Didius

---

### Post by J V on 2010-04-07
> **hatridge said:**
> Hi...No matter what I do in my terminal I am getting errors. I used restricted extras for an example. Please help as it is limiting my ability to install software....

jim@jim-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**ubuntu-restricted-extras is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-evolution (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gtkmozembed (2.25.3-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gtkmozembed (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-wnck (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-evolution
 python-gtkmozembedthis? If falcos advice doesn't work, do a sudo apt-get purge on the packets causing errors, and try to reinstall...

---

### Post by hatridge on 2010-04-09
jim@jim-desktop:~$ sudo dpkg --configure -a
[sudo] password for jim: 
Setting up python-wnck (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-evolution (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gtkmozembed (2.25.3-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gtkmozembed (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-wnck
 python-evolution
 python-gtkmozembed
jim@jim-desktop:~$ 
 

  I get the same errors no matter what the install or what ever I do in the terminal

---

### Post by hatridge on 2010-04-09
Ok if I try to purge I get this....

jim@jim-desktop:~$ sudo apt-get purge python-gtkmozembed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  python-gtkmozembed*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 336kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 60%
dpkg: warning: files list file for package `libemeraldengine0' missing, assuming package has no files currently installed.
(Reading database ... 211393 files and directories currently installed.)
Removing python-gtkmozembed ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-gtkmozembed (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-gtkmozembed
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-desktop:~$ 



Now what?

---

### Post by ndstate on 2010-05-18
I dont know if its applicable to your situation or not, but I had similar problems and [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096) fixed it for me.

Good luck

---

### Post by hatridge on 2010-05-18
Hello, and thanks. I am tempted to write solved, however that's not entirely true. I ungraded from 9.01 to 10.04 BETA, and I liked the previous Ubuntu better. I reinstalled and now everything seems much more stable. Terminal works great.

---

