---
title: "Ltsp Server Update"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by send2iwan on 2008-08-01
Good day everyone,

I am trying to update my Ltsp server from Gutsy to Hardy.
Everything ok only the last update, ltspfsd error come.

Can someone help or give a hint. sorry for bad english.

thanks.



iwan@ubuntu:~$ sudo chroot /opt/ltsp/i386/ apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  ltspfsd
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/19.0kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 20061 files and directories currently installed.)
Preparing to replace ltspfsd 0.5-0ubuntu2 (using .../ltspfsd_0.5.0~bzr20080109-3ubuntu3_i386.deb) ...
rm: cannot remove `/etc/udev/rules.d/88-ltsp.rules': No such file or directory
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/ltspfsd_0.5.0~bzr20080109-3ubuntu3_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/ltspfsd_0.5.0~bzr20080109-3ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

