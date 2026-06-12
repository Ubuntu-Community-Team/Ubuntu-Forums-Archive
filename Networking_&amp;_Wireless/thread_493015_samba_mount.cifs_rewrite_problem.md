---
title: "samba mount.cifs rewrite problem"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by s2p_ on 2007-07-05
when mounting a cifs share I get rewrite problems with various software : the first save is ok, subsequent saves produce errors.
The simplest way to reproduce the error is with vim : create a new file on a cifs network share (mounted using fstab entry like : //server/share /winshare      cifs    credentials=/root/smbcred,uid=test,gid=users,file_mode=0777,dir_mode=0777 0 0). The first save occurs normally, the next saves automatically trigger a warning message:

WARNING: The file has been changed since reading it!!!
Do you really want to overwrite to it (y/n)?

responding yes save the file correctly.
The same occurs with openoffice but not automatically. Whereas in eclipse it triggers a dialog box for each save (labelled "Update conflict" : The file 'eclipse_test/test01.rb' has been changed on the file system. Do you want to overwrite the changes).

I installed samba (containing mount.cifs) using apt-get on ubuntu Feisty (7.04), but the problem appeared before on ubuntu 6.06 and even on other distros (opensuse 10.0).

Does anyone running ubuntu have a working mount.cifs configuration that does not produce this kind of errors ? If no, does anyone have experience compiling samba from source to experiment different configure options ?


relative posts:
[http://www.aptana.com/trac/ticket/518](http://www.aptana.com/trac/ticket/518)
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=137011](https://bugs.eclipse.org/bugs/show_bug.cgi?id=137011)
[https://bugzilla.samba.org/show_bug.cgi?id=2673](https://bugzilla.samba.org/show_bug.cgi?id=2673)

---

### Post by s2p_ on 2007-07-06
Hi,

well I find another related post : [http://groups.google.com/group/cfeclipse-users/browse_thread/thread/5aea36c834278c1c](http://groups.google.com/group/cfeclipse-users/browse_thread/thread/5aea36c834278c1c)
The reply from pasholy2001 is especially interesting : he suggests that there's indeed a problem with cifs up to version 1.48a. My running ubuntu feisty machines have by default 1.47... so I tried to compile the external kernel module without success (I've never done this kind of operations before and my knowledge about the kernel or the compilation of external modules is limited).

=> Can someone the steps to update cifs external module under feisty to 1.48a ?

Thanks,

---

### Post by MikeMay on 2007-07-14
I have the same problem with a AirPort Extreme ...

Does anybody have a sulution?

---

