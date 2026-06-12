---
title: "FUSE 2.8.1 Wont Install"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2009-11-21
After manually installing Fuse, to support plptools, "clearinstall" ends with the following info and the progam isn't loaded. 

QUOTE
make[2]: Entering directory `/usr/local/src/fuse-2.8.1'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'fuse.pc' '/usr/local/lib/pkgconfig/fuse.pc'
make[2]: Leaving directory `/usr/local/src/fuse-2.8.1'
make[1]: Leaving directory `/usr/local/src/fuse-2.8.1'

======================== Installation successful ==========================

grep: /var/tmp/tmp.emCqNjFQbs/newfile: No such file or directory
Copying files to the temporary directory...OK
Stripping ELF binaries and libraries...OK
Compressing man pages...OK
Building file list...OK
Building Debian package...OK
Installing Debian package... FAILED!
*** Failed to install the package
Do you want to see the log file?  [y]:y
(Reading database ... 145514 files and directories currently installed.)
Unpacking fuse (from .../fuse_2.8.1-1_amd64.deb) ...
dpkg: fuse: warning - conffile `etc/udev' is not a plain file or symlink (= `/etc/udev')
dpkg: fuse: warning - conffile `etc/udev/rules.d' is not a plain file or symlink (= `/etc/udev/rules.d')
dpkg: fuse: warning - conffile `etc/init.d' is not a plain file or symlink (= `/etc/init.d')
dpkg: error processing /usr/local/src/fuse-2.8.1/fuse_2.8.1-1_amd64.deb (--install):
 trying to overwrite `/sbin/mount.fuse', which is also in package fuse-utils
Errors were encountered while processing:
 /usr/local/src/fuse-2.8.1/fuse_2.8.1-1_amd64.deb

QUOTE

Anyone any idea what I've done wrong? or is there a bug?

PS How do I create these scolling boxes in a thread?

---

