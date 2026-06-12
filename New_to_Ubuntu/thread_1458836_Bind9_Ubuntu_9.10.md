---
title: "Bind9 Ubuntu 9.10"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by happytimelogan on 2010-04-20
basically I was installing loads of server software because I'm trying to learn how to set stuff up like apache, webmin and samba and there was some sort of conflict with the following package

gadmin-bind
gadmin-dbg
bind9
& something else but I cant remember.

Anyways it meant that I could no longer run synaptic or even in terminal sudo apt-get update / install bla bla bla...

so I managed to do sudo apt-get remove gadmin-bind --purge and gadmin-bdg the same way.. but when I try to remove bind9 I get the following text in the terminal:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtsmux0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bind9
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 860kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169951 files and directories currently installed.)
Removing bind9 ...
 * Stopping domain name service... bind9                                        resolvconf: Error: /etc/resolv.conf must be a symlink
invoke-rc.d: initscript bind9, action "stop" failed.
dpkg: error processing bind9 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas...?

---

### Post by jaco223 on 2010-04-20
Try this:

```
sudo apt-get remove --purge (package name)

```Also be aware of case sensitive Y/n

You can try killing the bind9 process using system monitor, then try uninstalling it.

---

### Post by happytimelogan on 2010-04-21
Thank you!
I'll try this out when I get home.

---

### Post by happytimelogan on 2010-04-21
> **jaco223 said:**
> Try this:

```
sudo apt-get remove --purge (package name)

```Also be aware of case sensitive Y/n

You can try killing the bind9 process using system monitor, then try uninstalling it.

OK I made sure bind 9 isnt running and capitalised the Y in Y/n and now I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtsmux0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bind9*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 860kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 169951 files and directories currently installed.)
Removing bind9 ...
 * Stopping domain name service... bind9                                        resolvconf: Error: /etc/resolv.conf must be a symlink
invoke-rc.d: initscript bind9, action "stop" failed.
dpkg: error processing bind9 (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)

though it says stop failed so maybe its running in such a way that system monitor doesnt see it??

---

