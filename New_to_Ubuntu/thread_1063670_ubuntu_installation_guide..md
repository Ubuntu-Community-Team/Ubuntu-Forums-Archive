---
title: "ubuntu installation guide."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by garrydog on 2009-02-08
Hi
I am trying to work through the ubuntu installation guide,to try to install an ATI driver but I am stuck on one of the commands .The command is                                                                                                  sudo dpkg -i xorg-driver-fglrx_8.573-0ubuntu1_i386.deb fglrx-kernel-source_8.573-0ubuntu1_i386.deb fglrx-amdcccle_8.573-0ubuntu1_i386.deb 
I have checked that the DKMS is installed,and it is.

is this command OK should it work.

This is the readout,

david@david-desktop:~$ sudo dpkg -i xorg-driver-fglrx_8.573-0ubuntu1_i386.deb fglrx-kernel-source_8.573-0ubuntu1_i386.deb fglrx-amdcccle_8.573-0ubuntu1_i386.deb 
[sudo] password for david: 
dpkg: error processing xorg-driver-fglrx_8.573-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.573-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.573-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.573-0ubuntu1_i386.deb
 fglrx-kernel-source_8.573-0ubuntu1_i386.deb
 fglrx-amdcccle_8.573-0ubuntu1_i386.deb
david@david-desktop:~$

---

### Post by carml on 2009-02-08
Check if you writed right in the terminal.Is that package avaible in the repository or you downloaded it from ATI website?

---

