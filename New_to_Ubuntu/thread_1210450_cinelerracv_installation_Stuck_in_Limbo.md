---
title: "cinelerracv installation Stuck in Limbo"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by justinmiller87 on 2009-07-11
I added an external repository (Akirad), and attempted to install cinelerracv. Somewhere along the lines, something happened and now it won't install or uninstall, but is stuck attempting to do both. Whenever I do an update and upgrade I get the following:
```
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
If I try to install again I get this:
```
justin@justin:~$ sudo apt-get install cinelerracv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cinelerracv is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cinelerracv (2.1.1-git20090428akirad3) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerracv (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
If I try to remove it I get:
```
justin@justin:~$ sudo apt-get remove cinelerracv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cinelerracv
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 22.8MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 225337 files and directories currently installed.)
Removing cinelerracv ...
Description:	Ubuntu 9.04
locale "en_US.ISO-8859-15" not in archive
locale "ru_RU.KOI8-R" not in archive
 Removing any system startup links for /etc/init.d/cinestart ...
rm: cannot remove `/usr/share/applications/cinelerra-admin.desktop': No such file or directory
dpkg: error processing cinelerracv (--remove):
 subprocess post-removal script returned error exit status 1
Processing triggers for menu ...
Processing triggers for man-db ...
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions on getting it to work to either complete the install or the uninstall? I don't really care which one at this point. I just want it to stop pestering me.

Thanks.

---

### Post by shifty_powers on 2009-07-11
try

```
sudo dpkg --configure -a
```

---

### Post by justinmiller87 on 2009-07-11
Here's what I got:
```
justin@justin:~$ sudo dpkg --configure -a
Setting up cinelerracv (2.1.1-git20090428akirad3) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerracv (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerracv
```

---

### Post by justinmiller87 on 2009-07-13
Bump. Anyone else have a suggestion?

---

