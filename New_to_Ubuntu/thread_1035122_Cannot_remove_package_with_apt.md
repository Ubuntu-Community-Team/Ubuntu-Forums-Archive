---
title: "Cannot remove package with apt"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by slacker9876 on 2009-01-09
I an trying to remove postfix because I was not able to get the desired app configured and working with it. when I try to remove it, or process anything with apt I get an error code:

```
root@BROCO-WS001:/home/cbyrne# apt-get remove postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  postfix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3265kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123173 files and directories currently installed.)
Removing postfix ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error processing postfix (--remove):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@BROCO-WS001:/home/cbyrne# 

```Is there a way to force removal? How should I proceed?

---

### Post by Michael.Godawski on 2009-01-09
hi,

are you always doing things as root? Pretty dangerous:D

What output does this give you?
```

sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by slacker9876 on 2009-01-09
I do manage packages as root, but on from the ubuntu repositories. Is there a problem with that?

cbyrne@BROCO-WS001:~$ sudo apt-get install -f
[sudo] password for cbyrne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.5.5-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
cbyrne@BROCO-WS001:~$ sudo dpkg --configure -a
cbyrne@BROCO-WS001:~$

---

### Post by slacker9876 on 2009-01-09
Fixed with [http://ubuntuforums.org/archive/index.php/t-1014061.html](http://ubuntuforums.org/archive/index.php/t-1014061.html) 

I guess I should have Googled the error, sorry.

---

