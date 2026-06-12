---
title: "[SOLVED] Problems installing Packages in order to install WUSB54G wireless adapter"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2006-09-19
Hello everyone, and I do apologize if this is already posted somewhere that I missed. I have been trying for about 2 weeks now to get my WUSB54G wireless network adapter to be recognized on my Ubuntu 6.06 system. In System->Administration->Networking there is no wireless networking devices recognized. I am trying to follow the instructions on this post ([http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)) but at the part where you are supposed to install the build-essentials and kernel headers development tools I run into some problems. Here are the errors I receive when I try to install the packages:

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

build-essential:
 Depends: libc6-dev  but it is not installable or
 	libc-dev  but it is not installable
 Depends: gcc but it is not going to be installed
 Depends: g++ but it is not going to be installed

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

g++:
 Depends: cpp (>=4:4.0.3-1) but it is not installable
 Depends: gcc but it is not going to be installed
 Depends: g++-4.0 but it is not going to be installed
 Depends: gcc-4.0 (>=4.0.3) but it is not installable

*This error occurs after I try to install the make command by itself with the few other packages it would allow me to mark.*

The following problems were found on your system:

W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/i/isdnutils/libcapi20-3_3.8.2005-12-06-2ubuntu4_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/i/isdnutils/capiutils_3.8.2005-12-06-2ubuntu4_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/restricted/l/linux-restricted-modules-2.6.15/avm-fritz-firmware-2.6.15-23_3.11+2.6.15.11-1_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/restricted/l/linux-meta/avm-fritz-firmware_2.6.15.22_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/b/bpalogin/bpalogin_2.0.2-6ubuntu1_i386.deb
  MD5Sum mismatch


   I'm not quite sure what to do. Is it a problem with the disk? Is there something wrong with my installation? Any suggestions would be appreciated. Thanks for the help!

---

