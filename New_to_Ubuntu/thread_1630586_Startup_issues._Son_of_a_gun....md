---
title: "Startup issues. Son of a gun..."
date: 2010-11-25
forum: New to Ubuntu
---

### Post by SebSmith on 2010-11-25
whenever i start up my computer i enter my bios password, the the grub loader pops up.

-first of all, i like to reduce the amount of kernals i have to choose from.

then after i choose the selected kernal, it goes to a black balck screen with nothing except for a white flashing line in the top left. it remains like the for a good 5 seconds at least. and error message shows so fast i can't even read it. but then it loads into the login screen no problem.

the problem i have with this is that the whole awesomeness and braggablility of ubuntu was showing the startup time. i havent been able to show off my computer and spread the word of ubuntu because im embarrassed that it happens, and that im unaware of how to fix it.

the problem started when i was messing with the grub loader file in order to put a sweet black and orange ubuntu image in the background of the grub loader and changed the font to white. i only changed what i knew was ok to change. 

please somebody figure this out for me! thank you!

---

### Post by pawhtiobo on 2010-11-25
Hi :)

The easiest way to remove the amount of kernels is to install Ubuntu tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

[IMG]http://static.ubuntu.hamdi.web.id/wp-content/uploads/2009/04/clean-kernel.png[/IMG]

Choose the versions you want to remove.

About the error you see (don't see :)) you need to check the logs in **/var/log/ **and then we can find out whats wrong.

See ya...

---

### Post by fslezak on 2010-11-25
I don't think it is an error message. Sometimes Ubuntu flashes startup messages. It is OK and NORMAL for Ubuntu to do this.

---

### Post by madjr on 2010-11-25
yes, ubuntu-tweak is great.

but what you also want is to hide grub and make it pass by super fast

dont worry you can get into grub if you hit scape!

works well

install **startup manager** from the software center

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by SebSmith on 2010-12-01
> **pawhtiobo said:**
> Hi :)

The easiest way to remove the amount of kernels is to install Ubuntu tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

[IMG]http://static.ubuntu.hamdi.web.id/wp-content/uploads/2009/04/clean-kernel.png[/IMG]

Choose the versions you want to remove.

About the error you see (don't see :)) you need to check the logs in **/var/log/ **and then we can find out whats wrong.

See ya...



if you are talking about /var/log/bootsrap.log
```

Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5ubuntu4_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_5ubuntu4_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.21_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.; however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.21) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (5ubuntu4) ...

dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 101 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu1 (using .../dpkg_1.14.24ubuntu1_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: dpkg: dependency problems, but configuring anyway as you request:
 dpkg depends on libc6 (>= 2.; however:
  Package libc6 is not installed.
 dpkg depends on coreutils (>= 5.93-1); however:
  Package coreutils is not installed.
 dpkg depends on lzma; however:
  Package lzma is not installed.
Setting up dpkg (1.14.24ubuntu1) ...

Selecting previously deselected package libc6.
(Reading database ... 342 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.9-4ubuntu6_i386.deb) ...
dpkg: libc6: dependency problems, but configuring anyway as you request:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on findutils (>= 4.4.0-2ubuntu2); however:
  Package findutils is not installed.
Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package perl-base.
(Reading database ... 696 files and directories currently installed.)
Unpacking perl-base (from .../perl-base_5.10.0-19ubuntu1_i386.deb) ...
Setting up perl-base (5.10.0-19ubuntu1) ...
Selecting previously deselected package mawk.
(Reading database ... 1287 files and directories currently installed.)
Unpacking mawk (from .../mawk_1.3.3-13ubuntu1_i386.deb) ...
Setting up mawk (1.3.3-13ubuntu1) ...

Selecting previously deselected package debconf.
(Reading database ... 1306 files and directories currently installed.)
Unpacking debconf (from .../debconf_1.5.26ubuntu3_all.deb) ...
dpkg: debconf: dependency problems, but configuring anyway as you request:
 debconf depends on debconf-i18n | debconf-english; however:
  Package debconf-i18n is not installed.
  Package debconf-english is not installed.
Setting up debconf (1.5.26ubuntu3) ...

(Reading database ... 1484 files and directories currently installed.)
Preparing to replace base-files 5ubuntu4 (using .../base-files_5ubuntu4_i386.deb) ...
Unpacking replacement base-files ...
Preparing to replace base-passwd 3.5.21 (using .../base-passwd_3.5.21_i386.deb) ...
Unpacking replacement base-passwd ...
Selecting previously deselected package bash.
dpkg: regarding .../bash_3.2-5ubuntu1_i386.deb containing bash, pre-dependency problem:
 bash pre-depends on libncurses5 (>= 5.6+20071006-3)
dpkg: warning - ignoring pre-dependency problem !
Unpacking bash (from .../bash_3.2-5ubuntu1_i386.deb) ...
Selecting previously deselected package bsdutils.
Unpacking bsdutils (from .../bsdutils_1%3a2.14.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package coreutils.
dpkg: regarding .../coreutils_6.10-6ubuntu1_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libacl1 (>= 2.2.11-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../coreutils_6.10-6ubuntu1_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libselinux1
  libselinux1 is not installed.
dpkg: warning - ignoring pre-dependency problem !
Unpacking coreutils (from .../coreutils_6.10-6ubuntu1_i386.deb) ...
No diversion `any diversion of /usr/share/man/man1/md5sum.textutils.1.gz', none removed
No diversion `any diversion of /usr/bin/md5sum.textutils', none removed
Selecting previously deselected package dash.
Unpacking dash (from .../dash_0.5.4-12ubuntu2_i386.deb) ...
Preparing to replace debconf 1.5.26ubuntu3 (using .../debconf_1.5.26ubuntu3_all.deb) ...
Unpacking replacement debconf ...
Selecting previously deselected package debconf-i18n.
Unpacking debconf-i18n (from .../debconf-i18n_1.5.26ubuntu3_all.deb) ...
Selecting previously deselected package debianutils.
Unpacking debianutils (from .../debianutils_2.30ubuntu3_i386.deb) ...
Selecting previously deselected package diff.
Unpacking diff (from .../diff_2.8.1-12ubuntu1_i386.deb) ...
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
  coreutils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning - ignoring pre-dependency problem !
Preparing to replace dpkg 1.14.24ubuntu1 (using .../dpkg_1.14.24ubuntu1_i386.deb) ...
Unpacking replacement dpkg ...
Selecting previously deselected package e2fslibs.
Unpacking e2fslibs (from .../e2fslibs_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package e2fsprogs.
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on e2fslibs (>= 1.41.4)
  e2fslibs is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libblkid1 (>= 1.40)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libcomerr2 (>= 1.34)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libss2 (>= 1.34)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libuuid1 (>= 1.15)
dpkg: warning - ignoring pre-dependency problem !
Unpacking e2fsprogs (from .../e2fsprogs_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package findutils.
Unpacking findutils (from .../findutils_4.4.0-2ubuntu4_i386.deb) ...
Selecting previously deselected package gcc-4.3-base.
Unpacking gcc-4.3-base (from .../gcc-4.3-base_4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package grep.
dpkg: regarding .../grep_2.5.3~dfsg-6ubuntu1_i386.deb containing grep, pre-dependency problem:
 grep pre-depends on libpcre3 (>= 7.4)
dpkg: warning - ignoring pre-dependency problem !
Unpacking grep (from .../grep_2.5.3~dfsg-6ubuntu1_i386.deb) ...
Selecting previously deselected package gzip.
Unpacking gzip (from .../gzip_1.3.12-6ubuntu2_i386.deb) ...
Selecting previously deselected package hostname.
Unpacking hostname (from .../hostname_2.95_i386.deb) ...
Selecting previously deselected package initscripts.
Unpacking initscripts (from .../initscripts_2.86.ds1-61ubuntu11_i386.deb) ...
Selecting previously deselected package libacl1.
Unpacking libacl1 (from .../libacl1_2.2.47-2_i386.deb) ...
Selecting previously deselected package libattr1.
Unpacking libattr1 (from .../libattr1_1%3a2.4.43-1_i386.deb) ...
Selecting previously deselected package libblkid1.
Unpacking libblkid1 (from .../libblkid1_1.41.4-1ubuntu1_i386.deb) ...
Preparing to replace libc6 2.9-4ubuntu6 (using .../libc6_2.9-4ubuntu6_i386.deb) ...
Unpacking replacement libc6 ...
Selecting previously deselected package libcomerr2.
Unpacking libcomerr2 (from .../libcomerr2_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libdb4.7.
Unpacking libdb4.7 (from .../libdb4.7_4.7.25-6ubuntu1_i386.deb) ...
Selecting previously deselected package libgcc1.
Unpacking libgcc1 (from .../libgcc1_1%3a4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package liblocale-gettext-perl.
Unpacking liblocale-gettext-perl (from .../liblocale-gettext-perl_1.05-4build1_i386.deb) ...
Selecting previously deselected package libncurses5.
Unpacking libncurses5 (from .../libncurses5_5.7+20090207-1ubuntu1_i386.deb) ...
Selecting previously deselected package libpam-modules.
dpkg: regarding .../libpam-modules_1.0.1-9ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libdb4.7
  libdb4.7 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../libpam-modules_1.0.1-9ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libpam0g (>= 0.99.7.1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../libpam-modules_1.0.1-9ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libselinux1 (>= 2.0.59)
dpkg: warning - ignoring pre-dependency problem !
Unpacking libpam-modules (from .../libpam-modules_1.0.1-9ubuntu1_i386.deb) ...
Selecting previously deselected package libpam-runtime.
Unpacking libpam-runtime (from .../libpam-runtime_1.0.1-9ubuntu1_all.deb) ...
Selecting previously deselected package libpam0g.
Unpacking libpam0g (from .../libpam0g_1.0.1-9ubuntu1_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_7.8-2ubuntu1_i386.deb) ...
Selecting previously deselected package libselinux1.
Unpacking libselinux1 (from .../libselinux1_2.0.65-5build1_i386.deb) ...
Selecting previously deselected package libsepol1.
Unpacking libsepol1 (from .../libsepol1_2.0.30-2ubuntu1_i386.deb) ...
Selecting previously deselected package libslang2.
Unpacking libslang2 (from .../libslang2_2.1.3-3ubuntu3_i386.deb) ...
Selecting previously deselected package libss2.
Unpacking libss2 (from .../libss2_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++6.
Unpacking libstdc++6 (from .../libstdc++6_4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package libtext-charwidth-perl.
Unpacking libtext-charwidth-perl (from .../libtext-charwidth-perl_0.04-5build1_i386.deb) ...
Selecting previously deselected package libtext-iconv-perl.
Unpacking libtext-iconv-perl (from .../libtext-iconv-perl_1.7-1build1_i386.deb) ...
Selecting previously deselected package libtext-wrapi18n-perl.
Unpacking libtext-wrapi18n-perl (from .../libtext-wrapi18n-perl_0.06-6_all.deb) ...
Selecting previously deselected package libuuid1.
Unpacking libuuid1 (from .../libuuid1_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libvolume-id1.
Unpacking libvolume-id1 (from .../libvolume-id1_141-1_i386.deb) ...
Selecting previously deselected package locales.
Unpacking locales (from .../locales_2.9+cvs20090214-7_all.deb) ...
Selecting previously deselected package login.
dpkg: regarding .../login_1%3a4.1.1-6ubuntu6_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam0g (>= 0.99.7.1)
  libpam0g is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../login_1%3a4.1.1-6ubuntu6_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-runtime
  libpam-runtime is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../login_1%3a4.1.1-6ubuntu6_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-modules
  libpam-modules is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking login (from .../login_1%3a4.1.1-6ubuntu6_i386.deb) ...
Selecting previously deselected package lsb-base.
Unpacking lsb-base (from .../lsb-base_3.2-20ubuntu4_all.deb) ...
Selecting previously deselected package lzma.
Unpacking lzma (from .../lzma_4.43-14ubuntu1_i386.deb) ...
Selecting previously deselected package makedev.
Unpacking makedev (from .../makedev_2.3.1-88_all.deb) ...
 Removing any system startup links for /etc/init.d/makedev ...
Preparing to replace mawk 1.3.3-13ubuntu1 (using .../mawk_1.3.3-13ubuntu1_i386.deb) ...
Unpacking replacement mawk ...
Selecting previously deselected package mktemp.
Unpacking mktemp (from .../archives/mktemp_1.5-9_i386.deb) ...
Selecting previously deselected package mount.
dpkg: regarding .../mount_2.14.2-1ubuntu4_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libselinux1 (>= 2.0.59)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../mount_2.14.2-1ubuntu4_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libsepol1 (>= 2.0.25)
  libsepol1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../mount_2.14.2-1ubuntu4_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libvolume-id1
  libvolume-id1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking mount (from .../mount_2.14.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package ncurses-base.
Unpacking ncurses-base (from .../ncurses-base_5.7+20090207-1ubuntu1_all.deb) ...
Selecting previously deselected package ncurses-bin.
dpkg: regarding .../ncurses-bin_5.7+20090207-1ubuntu1_i386.deb containing ncurses-bin, pre-dependency problem:
 ncurses-bin pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking ncurses-bin (from .../ncurses-bin_5.7+20090207-1ubuntu1_i386.deb) ...
Selecting previously deselected package passwd.
Unpacking passwd (from .../passwd_1%3a4.1.1-6ubuntu6_i386.deb) ...
Preparing to replace perl-base 5.10.0-19ubuntu1 (using .../perl-base_5.10.0-19ubuntu1_i386.deb) ...
Unpacking replacement perl-base ...
Selecting previously deselected package procps.
Unpacking procps (from .../procps_1%3a3.2.7-11ubuntu2_i386.deb) ...
Selecting previously deselected package python-minimal.
Unpacking python-minimal (from .../python-minimal_2.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package python2.6-minimal.
Unpacking python2.6-minimal (from .../python2.6-minimal_2.6.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package sed.
Unpacking sed (from .../archives/sed_4.1.5-8_i386.deb) ...
Selecting previously deselected package startup-tasks.
Unpacking startup-tasks (from .../startup-tasks_0.3.9-8_i386.deb) ...
Selecting previously deselected package system-services.
Unpacking system-services (from .../system-services_0.3.9-8_i386.deb) ...
Selecting previously deselected package sysv-rc.
Unpacking sysv-rc (from .../sysv-rc_2.86.ds1-61ubuntu11_all.deb) ...
Selecting previously deselected package sysvinit-utils.
Unpacking sysvinit-utils (from .../sysvinit-utils_2.86.ds1-61ubuntu11_i386.deb) ...
Selecting previously deselected package tar.
Unpacking tar (from .../archives/tar_1.20-1_i386.deb) ...
Selecting previously deselected package tzdata.
Unpacking tzdata (from .../tzdata_2009f-0ubuntu1_all.deb) ...
Selecting previously deselected package upstart.
dpkg: regarding .../upstart_0.3.9-8_i386.deb containing upstart, pre-dependency problem:
 upstart pre-depends on sysvinit-utils
  sysvinit-utils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking upstart (from .../upstart_0.3.9-8_i386.deb) ...
Selecting previously deselected package upstart-compat-sysv.
Unpacking upstart-compat-sysv (from .../upstart-compat-sysv_0.3.9-8_i386.deb) ...
Selecting previously deselected package upstart-logd.
Unpacking upstart-logd (from .../upstart-logd_0.3.9-8_i386.deb) ...
Selecting previously deselected package util-linux.
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libselinux1 (>= 2.0.59)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libslang2 (>= 2.0.7-1)
  libslang2 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libuuid1 (>= 1.05)
  libuuid1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on zlib1g (>= 1:1.1.4)
dpkg: warning - ignoring pre-dependency problem !
Unpacking util-linux (from .../util-linux_2.14.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package zlib1g.
Unpacking zlib1g (from .../zlib1g_1%3a1.2.3.3.dfsg-12ubuntu2_i386.deb) ...
Setting up sysv-rc (2.86.ds1-61ubuntu11) ...
Setting up gcc-4.3-base (4.3.3-5ubuntu4) ...

Setting up libc6 (2.9-4ubuntu6) ...

Setting up mktemp (1.5-9) ...
Setting up debianutils (2.30ubuntu3) ...

Setting up bsdutils (1:2.14.2-1ubuntu4) ...

Setting up libsepol1 (2.0.30-2ubuntu1) ...

Setting up tar (1.20-1) ...

Setting up zlib1g (1:1.2.3.3.dfsg-12ubuntu2) ...

Setting up locales (2.9+cvs20090214-7) ...

Setting up libgcc1 (1:4.3.3-5ubuntu4) ...

Setting up libncurses5 (5.7+20090207-1ubuntu1) ...

Setting up libattr1 (1:2.4.43-1) ...

Setting up sed (4.1.5- ...

Setting up base-passwd (3.5.21) ...

Setting up libcomerr2 (1.41.4-1ubuntu1) ...

Setting up mawk (1.3.3-13ubuntu1) ...

Setting up libdb4.7 (4.7.25-6ubuntu1) ...
Setting up hostname (2.95) ...
Setting up libacl1 (2.2.47-2) ...

Setting up python2.6-minimal (2.6.2-0ubuntu1) ...

Setting up libslang2 (2.1.3-3ubuntu3) ...

Setting up libss2 (1.41.4-1ubuntu1) ...

Setting up findutils (4.4.0-2ubuntu4) ...

Setting up gzip (1.3.12-6ubuntu2) ...

Setting up libpcre3 (7.8-2ubuntu1) ...

Setting up diff (2.8.1-12ubuntu1) ...
Setting up libvolume-id1 (141-1) ...
Setting up libselinux1 (2.0.65-5build1) ...

Setting up libstdc++6 (4.3.3-5ubuntu4) ...

Setting up dash (0.5.4-12ubuntu2) ...
Adding `diversion of /bin/sh to /bin/sh.distrib by dash'
Adding `diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash'

Setting up coreutils (6.10-6ubuntu1) ...

Setting up makedev (2.3.1-8 ...

Setting up lzma (4.43-14ubuntu1) ...
Setting up ncurses-base (5.7+20090207-1ubuntu1) ...
Setting up ncurses-bin (5.7+20090207-1ubuntu1) ...
Setting up mount (2.14.2-1ubuntu4) ...

Setting up e2fslibs (1.41.4-1ubuntu1) ...

Setting up grep (2.5.3~dfsg-6ubuntu1) ...
Setting up dpkg (1.14.24ubuntu1) ...

Setting up sysvinit-utils (2.86.ds1-61ubuntu11) ...
Setting up lsb-base (3.2-20ubuntu4) ...
Setting up procps (1:3.2.7-11ubuntu2) ...

Setting up python-minimal (2.6.2-0ubuntu1) ...
Setting up perl-base (5.10.0-19ubuntu1) ...
Setting up libtext-iconv-perl (1.7-1build1) ...
Setting up upstart (0.3.9- ...

Setting up liblocale-gettext-perl (1.05-4build1) ...
Setting up libtext-charwidth-perl (0.04-5build1) ...
Setting up libtext-wrapi18n-perl (0.06-6) ...
Setting up upstart-logd (0.3.9- ...
Setting up startup-tasks (0.3.9- ...
Setting up debconf-i18n (1.5.26ubuntu3) ...
Setting up debconf (1.5.26ubuntu3) ...

Setting up tzdata (2009f-0ubuntu1) ...

Current default timezone: 'Etc/UTC'
Local time is now:      Mon Apr 20 13:59:44 UTC 2009.
Universal Time is now:  Mon Apr 20 13:59:44 UTC 2009.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


Setting up libpam-runtime (1.0.1-9ubuntu1) ...

Setting up libpam0g (1.0.1-9ubuntu1) ...

Setting up libpam-modules (1.0.1-9ubuntu1) ...

Setting up base-files (5ubuntu4) ...

Setting up passwd (1:4.1.1-6ubuntu6) ...
Shadow passwords are now on.

Setting up bash (3.2-5ubuntu1) ...

Setting up login (1:4.1.1-6ubuntu6) ...

Setting up libuuid1 (1.41.4-1ubuntu1) ...

Setting up libblkid1 (1.41.4-1ubuntu1) ...

Setting up e2fsprogs (1.41.4-1ubuntu1) ...
Setting up util-linux (2.14.2-1ubuntu4) ...

Setting up initscripts (2.86.ds1-61ubuntu11) ...

Setting up upstart-compat-sysv (0.3.9- ...

Setting up system-services (0.3.9- ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package adduser.
(Reading database ... 5986 files and directories currently installed.)
Unpacking adduser (from .../adduser_3.110ubuntu5_all.deb) ...
Selecting previously deselected package apt.
Unpacking apt (from .../apt_0.7.20.2ubuntu6_i386.deb) ...
Selecting previously deselected package apt-utils.
Unpacking apt-utils (from .../apt-utils_0.7.20.2ubuntu6_i386.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.4.11.11-1ubuntu1_i386.deb) ...
Selecting previously deselected package busybox-initramfs.
Unpacking busybox-initramfs (from .../busybox-initramfs_1%3a1.10.2-2ubuntu7_i386.deb) ...
Selecting previously deselected package bzip2.
Unpacking bzip2 (from .../bzip2_1.0.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package ca-certificates.
Unpacking ca-certificates (from .../ca-certificates_20080809_all.deb) ...
Selecting previously deselected package console-setup.
Unpacking console-setup (from .../console-setup_1.28ubuntu8_all.deb) ...
Selecting previously deselected package console-terminus.
Unpacking console-terminus (from .../console-terminus_4.26-2.1_all.deb) ...
Selecting previously deselected package cpio.
Unpacking cpio (from .../cpio_2.9-15ubuntu1_i386.deb) ...
Selecting previously deselected package dhcp3-client.
Unpacking dhcp3-client (from .../dhcp3-client_3.1.1-5ubuntu8_i386.deb) ...
Selecting previously deselected package dhcp3-common.
Unpacking dhcp3-common (from .../dhcp3-common_3.1.1-5ubuntu8_i386.deb) ...
Selecting previously deselected package dmidecode.
Unpacking dmidecode (from .../dmidecode_2.9-1ubuntu1_i386.deb) ...
Selecting previously deselected package dmsetup.
Unpacking dmsetup (from .../dmsetup_2%3a1.02.27-4ubuntu5_i386.deb) ...
Selecting previously deselected package eject.
Unpacking eject (from .../eject_2.1.5+deb1+cvs20081104-5_i386.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../file_4.26-2ubuntu3_i386.deb) ...
Selecting previously deselected package gnupg.
Unpacking gnupg (from .../gnupg_1.4.9-3ubuntu1_i386.deb) ...
Selecting previously deselected package gpgv.
Unpacking gpgv (from .../gpgv_1.4.9-3ubuntu1_i386.deb) ...
Selecting previously deselected package ifupdown.
Unpacking ifupdown (from .../ifupdown_0.6.8ubuntu19_i386.deb) ...
Selecting previously deselected package initramfs-tools.
Unpacking initramfs-tools (from .../initramfs-tools_0.92bubuntu29_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 59: /sbin/vol_id: not found
Selecting previously deselected package iproute.
Unpacking iproute (from .../iproute_20080725-2_i386.deb) ...
Selecting previously deselected package iputils-ping.
Unpacking iputils-ping (from .../iputils-ping_3%3a20071127-1_i386.deb) ...
Selecting previously deselected package kbd.
Unpacking kbd (from .../kbd_1.14.1-4ubuntu4_i386.deb) ...
Selecting previously deselected package klibc-utils.
Unpacking klibc-utils (from .../klibc-utils_1.5.14-1~exp1ubuntu2_i386.deb) ...
Selecting previously deselected package klogd.
Unpacking klogd (from .../klogd_1.5-5ubuntu3_i386.deb) ...
Selecting previously deselected package laptop-detect.
Unpacking laptop-detect (from .../laptop-detect_0.13.7ubuntu1_i386.deb) ...
Selecting previously deselected package less.
Unpacking less (from .../archives/less_418-1_i386.deb) ...
Selecting previously deselected package libatm1.
Unpacking libatm1 (from .../libatm1_2.4.1-17.2_i386.deb) ...
Selecting previously deselected package libbz2-1.0.
Unpacking libbz2-1.0 (from .../libbz2-1.0_1.0.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package libc6-i686.
Unpacking libc6-i686 (from .../libc6-i686_2.9-4ubuntu6_i386.deb) ...
Selecting previously deselected package libcap2.
Unpacking libcap2 (from .../libcap2_2.11-2_i386.deb) ...
Selecting previously deselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.31-2_all.deb) ...
Selecting previously deselected package libcurl3-gnutls.
Unpacking libcurl3-gnutls (from .../libcurl3-gnutls_7.18.2-8ubuntu4_i386.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.12-4ubuntu1_i386.deb) ...
Selecting previously deselected package libdb4.6.
Unpacking libdb4.6 (from .../libdb4.6_4.6.21-12_i386.deb) ...
Selecting previously deselected package libdevmapper1.02.1.
Unpacking libdevmapper1.02.1 (from .../libdevmapper1.02.1_2%3a1.02.27-4ubuntu5_i386.deb) ...
Selecting previously deselected package libept0.
Unpacking libept0 (from .../libept0_0.5.26build1_i386.deb) ...
Selecting previously deselected package libfribidi0.
Unpacking libfribidi0 (from .../libfribidi0_0.10.9-1_i386.deb) ...
Selecting previously deselected package libgcrypt11.
Unpacking libgcrypt11 (from .../libgcrypt11_1.4.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package libgdbm3.
Unpacking libgdbm3 (from .../libgdbm3_1.8.3-4_i386.deb) ...
Selecting previously deselected package libgnutls26.
Unpacking libgnutls26 (from .../libgnutls26_2.4.2-6_i386.deb) ...
Selecting previously deselected package libgpg-error0.
Unpacking libgpg-error0 (from .../libgpg-error0_1.4-2ubuntu7_i386.deb) ...
Selecting previously deselected package libgpm2.
Unpacking libgpm2 (from .../libgpm2_1.20.4-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package libidn11.
Unpacking libidn11 (from .../libidn11_1.10-3_i386.deb) ...
Selecting previously deselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously deselected package libkeyutils1.
Unpacking libkeyutils1 (from .../libkeyutils1_1.2-9_i386.deb) ...
Selecting previously deselected package libklibc.
Unpacking libklibc (from .../libklibc_1.5.14-1~exp1ubuntu2_i386.deb) ...
Selecting previously deselected package libkrb53.
Unpacking libkrb53 (from .../libkrb53_1.6.dfsg.4~beta1-5ubuntu2_i386.deb) ...
Selecting previously deselected package libldap-2.4-2.
Unpacking libldap-2.4-2 (from .../libldap-2.4-2_2.4.15-1ubuntu3_i386.deb) ...
Selecting previously deselected package liblockfile1.
Unpacking liblockfile1 (from .../liblockfile1_1.08-3_i386.deb) ...
Selecting previously deselected package libmagic1.
Unpacking libmagic1 (from .../libmagic1_4.26-2ubuntu3_i386.deb) ...
Selecting previously deselected package libncursesw5.
Unpacking libncursesw5 (from .../libncursesw5_5.7+20090207-1ubuntu1_i386.deb) ...
Selecting previously deselected package libnewt0.52.
Unpacking libnewt0.52 (from .../libnewt0.52_0.52.2-11.3ubuntu3_i386.deb) ...
Selecting previously deselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.1.1-2ubuntu1_all.deb) ...
Selecting previously deselected package libpopt0.
Unpacking libpopt0 (from .../libpopt0_1.14-4_i386.deb) ...
Selecting previously deselected package libreadline5.
Unpacking libreadline5 (from .../libreadline5_5.2-4_i386.deb) ...
Selecting previously deselected package libsasl2-2.
Unpacking libsasl2-2 (from .../libsasl2-2_2.1.22.dfsg1-23ubuntu3_i386.deb) ...
Selecting previously deselected package libsasl2-modules.
Unpacking libsasl2-modules (from .../libsasl2-modules_2.1.22.dfsg1-23ubuntu3_i386.deb) ...
Selecting previously deselected package libsigc++-2.0-0c2a.
Unpacking libsigc++-2.0-0c2a (from .../libsigc++-2.0-0c2a_2.0.18-2_i386.deb) ...
Selecting previously deselected package libsqlite3-0.
Unpacking libsqlite3-0 (from .../libsqlite3-0_3.6.10-1_i386.deb) ...
Selecting previously deselected package libssl0.9.8.
Unpacking libssl0.9.8 (from .../libssl0.9.8_0.9.8g-15ubuntu3_i386.deb) ...
Selecting previously deselected package libtasn1-3.
Unpacking libtasn1-3 (from .../libtasn1-3_1.5-1_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package libusb-0.1-4.
Unpacking libusb-0.1-4 (from .../libusb-0.1-4_2%3a0.1.12-13_i386.deb) ...
Selecting previously deselected package libxapian15.
Unpacking libxapian15 (from .../libxapian15_1.0.7-4_i386.deb) ...
Selecting previously deselected package lockfile-progs.
Unpacking lockfile-progs (from .../lockfile-progs_0.1.11ubuntu2_i386.deb) ...
Selecting previously deselected package lsb-release.
Unpacking lsb-release (from .../lsb-release_3.2-20ubuntu4_all.deb) ...
Selecting previously deselected package mime-support.
Unpacking mime-support (from .../mime-support_3.44-1_all.deb) ...
Selecting previously deselected package module-init-tools.
Unpacking module-init-tools (from .../module-init-tools_3.7~pre9-2_i386.deb) ...
Selecting previously deselected package net-tools.
Unpacking net-tools (from .../net-tools_1.60-21ubuntu1_i386.deb) ...
Selecting previously deselected package netbase.
Unpacking netbase (from .../netbase_4.34ubuntu2_all.deb) ...
Selecting previously deselected package netcat.
Unpacking netcat (from .../netcat_1.10-38_all.deb) ...
Selecting previously deselected package netcat-traditional.
Unpacking netcat-traditional (from .../netcat-traditional_1.10-38_i386.deb) ...
Selecting previously deselected package ntpdate.
Unpacking ntpdate (from .../ntpdate_1%3a4.2.4p4+dfsg-7ubuntu5_i386.deb) ...
Selecting previously deselected package openssl.
Unpacking openssl (from .../openssl_0.9.8g-15ubuntu3_i386.deb) ...
Selecting previously deselected package perl.
Unpacking perl (from .../perl_5.10.0-19ubuntu1_i386.deb) ...
Selecting previously deselected package perl-modules.
Unpacking perl-modules (from .../perl-modules_5.10.0-19ubuntu1_all.deb) ...
Selecting previously deselected package python.
Unpacking python (from .../python_2.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package python2.6.
Unpacking python2.6 (from .../python2.6_2.6.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package readline-common.
Unpacking readline-common (from .../readline-common_5.2-4_all.deb) ...
Selecting previously deselected package sudo.
Unpacking sudo (from .../sudo_1.6.9p17-1ubuntu3_i386.deb) ...
Selecting previously deselected package sysklogd.
Unpacking sysklogd (from .../sysklogd_1.5-5ubuntu3_i386.deb) ...
Selecting previously deselected package tasksel.
Unpacking tasksel (from .../tasksel_2.73ubuntu18_all.deb) ...
Selecting previously deselected package tasksel-data.
Unpacking tasksel-data (from .../tasksel-data_2.73ubuntu18_all.deb) ...
Selecting previously deselected package ubuntu-keyring.
Unpacking ubuntu-keyring (from .../ubuntu-keyring_2008.03.04_all.deb) ...
Selecting previously deselected package ubuntu-minimal.
Unpacking ubuntu-minimal (from .../ubuntu-minimal_1.140_i386.deb) ...
Selecting previously deselected package udev.
Unpacking udev (from .../archives/udev_141-1_i386.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Selecting previously deselected package vim-common.
Unpacking vim-common (from .../vim-common_2%3a7.2.079-1ubuntu5_i386.deb) ...
Selecting previously deselected package vim-tiny.
Unpacking vim-tiny (from .../vim-tiny_2%3a7.2.079-1ubuntu5_i386.deb) ...
Selecting previously deselected package whiptail.
Unpacking whiptail (from .../whiptail_0.52.2-11.3ubuntu3_i386.deb) ...
Selecting previously deselected package xkb-data.
Unpacking xkb-data (from .../xkb-data_1.5-2ubuntu11_all.deb) ...
Setting up sudo (1.6.9p17-1ubuntu3) ...
No /etc/sudoers found... creating one for you.

Setting up gpgv (1.4.9-3ubuntu1) ...
Setting up module-init-tools (3.7~pre9-2) ...

Setting up libgdbm3 (1.8.3-4) ...

Setting up libtasn1-3 (1.5-1) ...

Setting up libpopt0 (1.14-4) ...

Setting up libusb-0.1-4 (2:0.1.12-13) ...

Setting up libgpg-error0 (1.4-2ubuntu7) ...

Setting up libssl0.9.8 (0.9.8g-15ubuntu3) ...

Setting up vim-common (2:7.2.079-1ubuntu5) ...

Setting up openssl (0.9.8g-15ubuntu3) ...

Setting up apt (0.7.20.2ubuntu6) ...

Setting up netbase (4.34ubuntu2) ...

Setting up libmagic1 (4.26-2ubuntu3) ...

Setting up libxapian15 (1.0.7-4) ...

Setting up dmidecode (2.9-1ubuntu1) ...
Setting up file (4.26-2ubuntu3) ...
Setting up libfribidi0 (0.10.9-1) ...

Setting up adduser (3.110ubuntu5) ...

Setting up libklibc (1.5.14-1~exp1ubuntu2) ...
Setting up libsqlite3-0 (3.6.10-1) ...

Setting up libkeyutils1 (1.2-9) ...

Setting up iproute (20080725-2) ...
Setting up libdevmapper1.02.1 (2:1.02.27-4ubuntu5) ...

Setting up libidn11 (1.10-3) ...

Setting up libatm1 (2.4.1-17.2) ...

Setting up klibc-utils (1.5.14-1~exp1ubuntu2) ...
Setting up libnewt0.52 (0.52.2-11.3ubuntu3) ...

Setting up libdb4.6 (4.6.21-12) ...
Setting up net-tools (1.60-21ubuntu1) ...
Setting up xkb-data (1.5-2ubuntu11) ...
Setting up libsigc++-2.0-0c2a (2.0.18-2) ...

Setting up netcat-traditional (1.10-3 ...

Setting up libgpm2 (1.20.4-3.1ubuntu1) ...

Setting up libept0 (0.5.26build1) ...

Setting up libncursesw5 (5.7+20090207-1ubuntu1) ...

Setting up eject (2.1.5+deb1+cvs20081104-5) ...
Setting up busybox-initramfs (1:1.10.2-2ubuntu7) ...
Setting up iputils-ping (3:20071127-1) ...
Setting up libbz2-1.0 (1.0.5-1ubuntu1) ...

Setting up libc6-i686 (2.9-4ubuntu6) ...

Setting up mime-support (3.44-1) ...

Setting up dhcp3-common (3.1.1-5ubuntu ...
Setting up apt-utils (0.7.20.2ubuntu6) ...

Setting up libkrb53 (1.6.dfsg.4~beta1-5ubuntu2) ...

Setting up cpio (2.9-15ubuntu1) ...

Setting up ca-certificates (20080809) ...
Updating certificates in /etc/ssl/certs....done.
Running hooks in /etc/ca-certificates/update.d....done.

Setting up vim-tiny (2:7.2.079-1ubuntu5) ...

Setting up less (418-1) ...

Setting up readline-common (5.2-4) ...

Setting up libcap2 (2.11-2) ...

Setting up netcat (1.10-3 ...
Setting up liblockfile1 (1.08-3) ...

Setting up laptop-detect (0.13.7ubuntu1) ...
Setting up libgcrypt11 (1.4.1-2ubuntu1) ...

Setting up bzip2 (1.0.5-1ubuntu1) ...

Setting up whiptail (0.52.2-11.3ubuntu3) ...
Setting up ifupdown (0.6.8ubuntu19) ...
ifupdown.postinst: Warning: No 'iface lo' definition found in /etc/network/interfaces
ifupdown.postinst: Warning: No 'auto lo' statement found in /etc/network/interfaces

Setting up dhcp3-client (3.1.1-5ubuntu ...

Setting up libreadline5 (5.2-4) ...

Setting up lockfile-progs (0.1.11ubuntu2) ...
Setting up libcwidget3 (0.5.12-4ubuntu1) ...

Setting up libgnutls26 (2.4.2-6) ...

Setting up aptitude (0.4.11.11-1ubuntu1) ...

Setting up ntpdate (1:4.2.4p4+dfsg-7ubuntu5) ...
Setting up python2.6 (2.6.2-0ubuntu1) ...

Setting up python (2.6.2-0ubuntu1) ...

Setting up lsb-release (3.2-20ubuntu4) ...

Setting up libsasl2-modules (2.1.22.dfsg1-23ubuntu3) ...
Setting up libsasl2-2 (2.1.22.dfsg1-23ubuntu3) ...

Setting up console-terminus (4.26-2.1) ...
Setting up sysklogd (1.5-5ubuntu3) ...
 * Starting system log daemon...

Warning: Fake start-stop-daemon called, doing nothing
   ...done.

Setting up libldap-2.4-2 (2.4.15-1ubuntu3) ...

Setting up klogd (1.5-5ubuntu3) ...
 * Starting kernel log daemon...

Warning: Fake start-stop-daemon called, doing nothing

Warning: Fake start-stop-daemon called, doing nothing
   ...done.

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up libcurl3-gnutls (7.18.2-8ubuntu4) ...

Setting up perl-modules (5.10.0-19ubuntu1) ...
Setting up console-setup (1.28ubuntu ...
 * Setting up console font and keymap...
   ...done.
update-initramfs: deferring update (trigger activated)

Setting up tasksel-data (2.73ubuntu1 ...
Setting up gnupg (1.4.9-3ubuntu1) ...
Setting up kbd (1.14.1-4ubuntu4) ...
 Removing any system startup links for /etc/init.d/console-screen.kbd.sh ...
update-initramfs: deferring update (trigger activated)

Setting up ubuntu-keyring (2008.03.04) ...
gpg: /etc/apt/trustdb.gpg: trustdb created
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 17 new signatures
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: Total number processed: 2
gpg:               imported: 1
gpg:         new signatures: 17
gpg: no ultimately trusted keys found
gpg: keyring `/usr/share/keyrings/ubuntu-archive-removed-keys.gpg' created

Setting up dmsetup (2:1.02.27-4ubuntu5) ...
update-initramfs: deferring update (trigger activated)

Setting up perl (5.10.0-19ubuntu1) ...

Setting up udev (141-1) ...
 * Stopping kernel event manager...

Warning: Fake start-stop-daemon called, doing nothing
   ...done.
 * Starting kernel event manager...

Warning: Fake start-stop-daemon called, doing nothing
   ...done.
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Setting up libio-string-perl (1.08-2) ...
Setting up libclass-accessor-perl (0.31-2) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up tasksel (2.73ubuntu1 ...

Setting up libparse-debianchangelog-perl (1.1.1-2ubuntu1) ...
Setting up ubuntu-minimal (1.140) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...



```


i am an absolute beginner for sure...

---

### Post by oldos2er on 2010-12-01
That's really a mess.  :)

Check Synaptic Package Manager (in menus System, Administration), Settings, Repositories, and make sure all repos under 'Downloadable from the Internet' are checked. Then run ```
sudo apt-get update && sudo apt-get safe-upgrade
``` in a terminal, and if there are errors please post the whole output here.

---

### Post by SebSmith on 2010-12-02
> **oldos2er said:**
> That's really a mess.  :)

Check Synaptic Package Manager (in menus System, Administration), Settings, Repositories, and make sure all repos under 'Downloadable from the Internet' are checked. Then run ```
sudo apt-get update && sudo apt-get safe-upgrade
``` in a terminal, and if there are errors please post the whole output here.



ok so i did what you said and the problem has worsened. it now loads to grub, i select my kernel and it loads to the black screen with blinky thing and top left, then loads to a second blank screen with blinky.

my boot.log is this:

```
fsck from util-linux-ng 2.17.2 
/dev/sda5: clean, 237157/9838592 files, 10043788/39353209 blocks 
 * Starting AppArmor profiles       [160G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 [154G[ OK ] 
 * Setting sensors limits       [160G  [154G[ OK ] 
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem 
Starting SmartLink Modem driver for: modem:1. 
Creating /dev/modem symlink, pointing to: /dev/ttySL0. 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
 * Starting User-mode networking switch uml_switch       [160G  
```


my bootstrap.log reads:

```
Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5ubuntu4_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_5ubuntu4_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.21_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.; however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.21) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (5ubuntu4) ...

dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 101 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu1 (using .../dpkg_1.14.24ubuntu1_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: dpkg: dependency problems, but configuring anyway as you request:
 dpkg depends on libc6 (>= 2.; however:
  Package libc6 is not installed.
 dpkg depends on coreutils (>= 5.93-1); however:
  Package coreutils is not installed.
 dpkg depends on lzma; however:
  Package lzma is not installed.
Setting up dpkg (1.14.24ubuntu1) ...

Selecting previously deselected package libc6.
(Reading database ... 342 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.9-4ubuntu6_i386.deb) ...
dpkg: libc6: dependency problems, but configuring anyway as you request:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on findutils (>= 4.4.0-2ubuntu2); however:
  Package findutils is not installed.
Setting up libc6 (2.9-4ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package perl-base.
(Reading database ... 696 files and directories currently installed.)
Unpacking perl-base (from .../perl-base_5.10.0-19ubuntu1_i386.deb) ...
Setting up perl-base (5.10.0-19ubuntu1) ...
Selecting previously deselected package mawk.
(Reading database ... 1287 files and directories currently installed.)
Unpacking mawk (from .../mawk_1.3.3-13ubuntu1_i386.deb) ...
Setting up mawk (1.3.3-13ubuntu1) ...

Selecting previously deselected package debconf.
(Reading database ... 1306 files and directories currently installed.)
Unpacking debconf (from .../debconf_1.5.26ubuntu3_all.deb) ...
dpkg: debconf: dependency problems, but configuring anyway as you request:
 debconf depends on debconf-i18n | debconf-english; however:
  Package debconf-i18n is not installed.
  Package debconf-english is not installed.
Setting up debconf (1.5.26ubuntu3) ...

(Reading database ... 1484 files and directories currently installed.)
Preparing to replace base-files 5ubuntu4 (using .../base-files_5ubuntu4_i386.deb) ...
Unpacking replacement base-files ...
Preparing to replace base-passwd 3.5.21 (using .../base-passwd_3.5.21_i386.deb) ...
Unpacking replacement base-passwd ...
Selecting previously deselected package bash.
dpkg: regarding .../bash_3.2-5ubuntu1_i386.deb containing bash, pre-dependency problem:
 bash pre-depends on libncurses5 (>= 5.6+20071006-3)
dpkg: warning - ignoring pre-dependency problem !
Unpacking bash (from .../bash_3.2-5ubuntu1_i386.deb) ...
Selecting previously deselected package bsdutils.
Unpacking bsdutils (from .../bsdutils_1%3a2.14.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package coreutils.
dpkg: regarding .../coreutils_6.10-6ubuntu1_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libacl1 (>= 2.2.11-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../coreutils_6.10-6ubuntu1_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libselinux1
  libselinux1 is not installed.
dpkg: warning - ignoring pre-dependency problem !
Unpacking coreutils (from .../coreutils_6.10-6ubuntu1_i386.deb) ...
No diversion `any diversion of /usr/share/man/man1/md5sum.textutils.1.gz', none removed
No diversion `any diversion of /usr/bin/md5sum.textutils', none removed
Selecting previously deselected package dash.
Unpacking dash (from .../dash_0.5.4-12ubuntu2_i386.deb) ...
Preparing to replace debconf 1.5.26ubuntu3 (using .../debconf_1.5.26ubuntu3_all.deb) ...
Unpacking replacement debconf ...
Selecting previously deselected package debconf-i18n.
Unpacking debconf-i18n (from .../debconf-i18n_1.5.26ubuntu3_all.deb) ...
Selecting previously deselected package debianutils.
Unpacking debianutils (from .../debianutils_2.30ubuntu3_i386.deb) ...
Selecting previously deselected package diff.
Unpacking diff (from .../diff_2.8.1-12ubuntu1_i386.deb) ...
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
  coreutils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.24ubuntu1_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning - ignoring pre-dependency problem !
Preparing to replace dpkg 1.14.24ubuntu1 (using .../dpkg_1.14.24ubuntu1_i386.deb) ...
Unpacking replacement dpkg ...
Selecting previously deselected package e2fslibs.
Unpacking e2fslibs (from .../e2fslibs_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package e2fsprogs.
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on e2fslibs (>= 1.41.4)
  e2fslibs is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libblkid1 (>= 1.40)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libcomerr2 (>= 1.34)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libss2 (>= 1.34)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.41.4-1ubuntu1_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libuuid1 (>= 1.15)
dpkg: warning - ignoring pre-dependency problem !
Unpacking e2fsprogs (from .../e2fsprogs_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package findutils.
Unpacking findutils (from .../findutils_4.4.0-2ubuntu4_i386.deb) ...
Selecting previously deselected package gcc-4.3-base.
Unpacking gcc-4.3-base (from .../gcc-4.3-base_4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package grep.
dpkg: regarding .../grep_2.5.3~dfsg-6ubuntu1_i386.deb containing grep, pre-dependency problem:
 grep pre-depends on libpcre3 (>= 7.4)
dpkg: warning - ignoring pre-dependency problem !
Unpacking grep (from .../grep_2.5.3~dfsg-6ubuntu1_i386.deb) ...
Selecting previously deselected package gzip.
Unpacking gzip (from .../gzip_1.3.12-6ubuntu2_i386.deb) ...
Selecting previously deselected package hostname.
Unpacking hostname (from .../hostname_2.95_i386.deb) ...
Selecting previously deselected package initscripts.
Unpacking initscripts (from .../initscripts_2.86.ds1-61ubuntu11_i386.deb) ...
Selecting previously deselected package libacl1.
Unpacking libacl1 (from .../libacl1_2.2.47-2_i386.deb) ...
Selecting previously deselected package libattr1.
Unpacking libattr1 (from .../libattr1_1%3a2.4.43-1_i386.deb) ...
Selecting previously deselected package libblkid1.
Unpacking libblkid1 (from .../libblkid1_1.41.4-1ubuntu1_i386.deb) ...
Preparing to replace libc6 2.9-4ubuntu6 (using .../libc6_2.9-4ubuntu6_i386.deb) ...
Unpacking replacement libc6 ...
Selecting previously deselected package libcomerr2.
Unpacking libcomerr2 (from .../libcomerr2_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libdb4.7.
Unpacking libdb4.7 (from .../libdb4.7_4.7.25-6ubuntu1_i386.deb) ...
Selecting previously deselected package libgcc1.
Unpacking libgcc1 (from .../libgcc1_1%3a4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package liblocale-gettext-perl.
Unpacking liblocale-gettext-perl (from .../liblocale-gettext-perl_1.05-4build1_i386.deb) ...
Selecting previously deselected package libncurses5.
Unpacking libncurses5 (from .../libncurses5_5.7+20090207-1ubuntu1_i386.deb) ...
Selecting previously deselected package libpam-modules.
dpkg: regarding .../libpam-modules_1.0.1-9ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libdb4.7
  libdb4.7 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../libpam-modules_1.0.1-9ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libpam0g (>= 0.99.7.1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../libpam-modules_1.0.1-9ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libselinux1 (>= 2.0.59)
dpkg: warning - ignoring pre-dependency problem !
Unpacking libpam-modules (from .../libpam-modules_1.0.1-9ubuntu1_i386.deb) ...
Selecting previously deselected package libpam-runtime.
Unpacking libpam-runtime (from .../libpam-runtime_1.0.1-9ubuntu1_all.deb) ...
Selecting previously deselected package libpam0g.
Unpacking libpam0g (from .../libpam0g_1.0.1-9ubuntu1_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_7.8-2ubuntu1_i386.deb) ...
Selecting previously deselected package libselinux1.
Unpacking libselinux1 (from .../libselinux1_2.0.65-5build1_i386.deb) ...
Selecting previously deselected package libsepol1.
Unpacking libsepol1 (from .../libsepol1_2.0.30-2ubuntu1_i386.deb) ...
Selecting previously deselected package libslang2.
Unpacking libslang2 (from .../libslang2_2.1.3-3ubuntu3_i386.deb) ...
Selecting previously deselected package libss2.
Unpacking libss2 (from .../libss2_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++6.
Unpacking libstdc++6 (from .../libstdc++6_4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package libtext-charwidth-perl.
Unpacking libtext-charwidth-perl (from .../libtext-charwidth-perl_0.04-5build1_i386.deb) ...
Selecting previously deselected package libtext-iconv-perl.
Unpacking libtext-iconv-perl (from .../libtext-iconv-perl_1.7-1build1_i386.deb) ...
Selecting previously deselected package libtext-wrapi18n-perl.
Unpacking libtext-wrapi18n-perl (from .../libtext-wrapi18n-perl_0.06-6_all.deb) ...
Selecting previously deselected package libuuid1.
Unpacking libuuid1 (from .../libuuid1_1.41.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package libvolume-id1.
Unpacking libvolume-id1 (from .../libvolume-id1_141-1_i386.deb) ...
Selecting previously deselected package locales.
Unpacking locales (from .../locales_2.9+cvs20090214-7_all.deb) ...
Selecting previously deselected package login.
dpkg: regarding .../login_1%3a4.1.1-6ubuntu6_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam0g (>= 0.99.7.1)
  libpam0g is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../login_1%3a4.1.1-6ubuntu6_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-runtime
  libpam-runtime is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../login_1%3a4.1.1-6ubuntu6_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-modules
  libpam-modules is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking login (from .../login_1%3a4.1.1-6ubuntu6_i386.deb) ...
Selecting previously deselected package lsb-base.
Unpacking lsb-base (from .../lsb-base_3.2-20ubuntu4_all.deb) ...
Selecting previously deselected package lzma.
Unpacking lzma (from .../lzma_4.43-14ubuntu1_i386.deb) ...
Selecting previously deselected package makedev.
Unpacking makedev (from .../makedev_2.3.1-88_all.deb) ...
 Removing any system startup links for /etc/init.d/makedev ...
Preparing to replace mawk 1.3.3-13ubuntu1 (using .../mawk_1.3.3-13ubuntu1_i386.deb) ...
Unpacking replacement mawk ...
Selecting previously deselected package mktemp.
Unpacking mktemp (from .../archives/mktemp_1.5-9_i386.deb) ...
Selecting previously deselected package mount.
dpkg: regarding .../mount_2.14.2-1ubuntu4_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libselinux1 (>= 2.0.59)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../mount_2.14.2-1ubuntu4_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libsepol1 (>= 2.0.25)
  libsepol1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../mount_2.14.2-1ubuntu4_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libvolume-id1
  libvolume-id1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking mount (from .../mount_2.14.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package ncurses-base.
Unpacking ncurses-base (from .../ncurses-base_5.7+20090207-1ubuntu1_all.deb) ...
Selecting previously deselected package ncurses-bin.
dpkg: regarding .../ncurses-bin_5.7+20090207-1ubuntu1_i386.deb containing ncurses-bin, pre-dependency problem:
 ncurses-bin pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking ncurses-bin (from .../ncurses-bin_5.7+20090207-1ubuntu1_i386.deb) ...
Selecting previously deselected package passwd.
Unpacking passwd (from .../passwd_1%3a4.1.1-6ubuntu6_i386.deb) ...
Preparing to replace perl-base 5.10.0-19ubuntu1 (using .../perl-base_5.10.0-19ubuntu1_i386.deb) ...
Unpacking replacement perl-base ...
Selecting previously deselected package procps.
Unpacking procps (from .../procps_1%3a3.2.7-11ubuntu2_i386.deb) ...
Selecting previously deselected package python-minimal.
Unpacking python-minimal (from .../python-minimal_2.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package python2.6-minimal.
Unpacking python2.6-minimal (from .../python2.6-minimal_2.6.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package sed.
Unpacking sed (from .../archives/sed_4.1.5-8_i386.deb) ...
Selecting previously deselected package startup-tasks.
Unpacking startup-tasks (from .../startup-tasks_0.3.9-8_i386.deb) ...
Selecting previously deselected package system-services.
Unpacking system-services (from .../system-services_0.3.9-8_i386.deb) ...
Selecting previously deselected package sysv-rc.
Unpacking sysv-rc (from .../sysv-rc_2.86.ds1-61ubuntu11_all.deb) ...
Selecting previously deselected package sysvinit-utils.
Unpacking sysvinit-utils (from .../sysvinit-utils_2.86.ds1-61ubuntu11_i386.deb) ...
Selecting previously deselected package tar.
Unpacking tar (from .../archives/tar_1.20-1_i386.deb) ...
Selecting previously deselected package tzdata.
Unpacking tzdata (from .../tzdata_2009f-0ubuntu1_all.deb) ...
Selecting previously deselected package upstart.
dpkg: regarding .../upstart_0.3.9-8_i386.deb containing upstart, pre-dependency problem:
 upstart pre-depends on sysvinit-utils
  sysvinit-utils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking upstart (from .../upstart_0.3.9-8_i386.deb) ...
Selecting previously deselected package upstart-compat-sysv.
Unpacking upstart-compat-sysv (from .../upstart-compat-sysv_0.3.9-8_i386.deb) ...
Selecting previously deselected package upstart-logd.
Unpacking upstart-logd (from .../upstart-logd_0.3.9-8_i386.deb) ...
Selecting previously deselected package util-linux.
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libselinux1 (>= 2.0.59)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libslang2 (>= 2.0.7-1)
  libslang2 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libuuid1 (>= 1.05)
  libuuid1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.14.2-1ubuntu4_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on zlib1g (>= 1:1.1.4)
dpkg: warning - ignoring pre-dependency problem !
Unpacking util-linux (from .../util-linux_2.14.2-1ubuntu4_i386.deb) ...
Selecting previously deselected package zlib1g.
Unpacking zlib1g (from .../zlib1g_1%3a1.2.3.3.dfsg-12ubuntu2_i386.deb) ...
Setting up sysv-rc (2.86.ds1-61ubuntu11) ...
Setting up gcc-4.3-base (4.3.3-5ubuntu4) ...

Setting up libc6 (2.9-4ubuntu6) ...

Setting up mktemp (1.5-9) ...
Setting up debianutils (2.30ubuntu3) ...

Setting up bsdutils (1:2.14.2-1ubuntu4) ...

Setting up libsepol1 (2.0.30-2ubuntu1) ...

Setting up tar (1.20-1) ...

Setting up zlib1g (1:1.2.3.3.dfsg-12ubuntu2) ...

Setting up locales (2.9+cvs20090214-7) ...

Setting up libgcc1 (1:4.3.3-5ubuntu4) ...

Setting up libncurses5 (5.7+20090207-1ubuntu1) ...

Setting up libattr1 (1:2.4.43-1) ...

Setting up sed (4.1.5- ...

Setting up base-passwd (3.5.21) ...

Setting up libcomerr2 (1.41.4-1ubuntu1) ...

Setting up mawk (1.3.3-13ubuntu1) ...

Setting up libdb4.7 (4.7.25-6ubuntu1) ...
Setting up hostname (2.95) ...
Setting up libacl1 (2.2.47-2) ...

Setting up python2.6-minimal (2.6.2-0ubuntu1) ...

Setting up libslang2 (2.1.3-3ubuntu3) ...

Setting up libss2 (1.41.4-1ubuntu1) ...

Setting up findutils (4.4.0-2ubuntu4) ...

Setting up gzip (1.3.12-6ubuntu2) ...

Setting up libpcre3 (7.8-2ubuntu1) ...

Setting up diff (2.8.1-12ubuntu1) ...
Setting up libvolume-id1 (141-1) ...
Setting up libselinux1 (2.0.65-5build1) ...

Setting up libstdc++6 (4.3.3-5ubuntu4) ...

Setting up dash (0.5.4-12ubuntu2) ...
Adding `diversion of /bin/sh to /bin/sh.distrib by dash'
Adding `diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash'

Setting up coreutils (6.10-6ubuntu1) ...

Setting up makedev (2.3.1-8 ...

Setting up lzma (4.43-14ubuntu1) ...
Setting up ncurses-base (5.7+20090207-1ubuntu1) ...
Setting up ncurses-bin (5.7+20090207-1ubuntu1) ...
Setting up mount (2.14.2-1ubuntu4) ...

Setting up e2fslibs (1.41.4-1ubuntu1) ...

Setting up grep (2.5.3~dfsg-6ubuntu1) ...
Setting up dpkg (1.14.24ubuntu1) ...

Setting up sysvinit-utils (2.86.ds1-61ubuntu11) ...
Setting up lsb-base (3.2-20ubuntu4) ...
Setting up procps (1:3.2.7-11ubuntu2) ...

Setting up python-minimal (2.6.2-0ubuntu1) ...
Setting up perl-base (5.10.0-19ubuntu1) ...
Setting up libtext-iconv-perl (1.7-1build1) ...
Setting up upstart (0.3.9- ...

Setting up liblocale-gettext-perl (1.05-4build1) ...
Setting up libtext-charwidth-perl (0.04-5build1) ...
Setting up libtext-wrapi18n-perl (0.06-6) ...
Setting up upstart-logd (0.3.9- ...
Setting up startup-tasks (0.3.9- ...
Setting up debconf-i18n (1.5.26ubuntu3) ...
Setting up debconf (1.5.26ubuntu3) ...

Setting up tzdata (2009f-0ubuntu1) ...

Current default timezone: 'Etc/UTC'
Local time is now:      Mon Apr 20 13:59:44 UTC 2009.
Universal Time is now:  Mon Apr 20 13:59:44 UTC 2009.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


Setting up libpam-runtime (1.0.1-9ubuntu1) ...

Setting up libpam0g (1.0.1-9ubuntu1) ...

Setting up libpam-modules (1.0.1-9ubuntu1) ...

Setting up base-files (5ubuntu4) ...

Setting up passwd (1:4.1.1-6ubuntu6) ...
Shadow passwords are now on.

Setting up bash (3.2-5ubuntu1) ...

Setting up login (1:4.1.1-6ubuntu6) ...

Setting up libuuid1 (1.41.4-1ubuntu1) ...

Setting up libblkid1 (1.41.4-1ubuntu1) ...

Setting up e2fsprogs (1.41.4-1ubuntu1) ...
Setting up util-linux (2.14.2-1ubuntu4) ...

Setting up initscripts (2.86.ds1-61ubuntu11) ...

Setting up upstart-compat-sysv (0.3.9- ...

Setting up system-services (0.3.9- ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package adduser.
(Reading database ... 5986 files and directories currently installed.)
Unpacking adduser (from .../adduser_3.110ubuntu5_all.deb) ...
Selecting previously deselected package apt.
Unpacking apt (from .../apt_0.7.20.2ubuntu6_i386.deb) ...
Selecting previously deselected package apt-utils.
Unpacking apt-utils (from .../apt-utils_0.7.20.2ubuntu6_i386.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.4.11.11-1ubuntu1_i386.deb) ...
Selecting previously deselected package busybox-initramfs.
Unpacking busybox-initramfs (from .../busybox-initramfs_1%3a1.10.2-2ubuntu7_i386.deb) ...
Selecting previously deselected package bzip2.
Unpacking bzip2 (from .../bzip2_1.0.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package ca-certificates.
Unpacking ca-certificates (from .../ca-certificates_20080809_all.deb) ...
Selecting previously deselected package console-setup.
Unpacking console-setup (from .../console-setup_1.28ubuntu8_all.deb) ...
Selecting previously deselected package console-terminus.
Unpacking console-terminus (from .../console-terminus_4.26-2.1_all.deb) ...
Selecting previously deselected package cpio.
Unpacking cpio (from .../cpio_2.9-15ubuntu1_i386.deb) ...
Selecting previously deselected package dhcp3-client.
Unpacking dhcp3-client (from .../dhcp3-client_3.1.1-5ubuntu8_i386.deb) ...
Selecting previously deselected package dhcp3-common.
Unpacking dhcp3-common (from .../dhcp3-common_3.1.1-5ubuntu8_i386.deb) ...
Selecting previously deselected package dmidecode.
Unpacking dmidecode (from .../dmidecode_2.9-1ubuntu1_i386.deb) ...
Selecting previously deselected package dmsetup.
Unpacking dmsetup (from .../dmsetup_2%3a1.02.27-4ubuntu5_i386.deb) ...
Selecting previously deselected package eject.
Unpacking eject (from .../eject_2.1.5+deb1+cvs20081104-5_i386.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../file_4.26-2ubuntu3_i386.deb) ...
Selecting previously deselected package gnupg.
Unpacking gnupg (from .../gnupg_1.4.9-3ubuntu1_i386.deb) ...
Selecting previously deselected package gpgv.
Unpacking gpgv (from .../gpgv_1.4.9-3ubuntu1_i386.deb) ...
Selecting previously deselected package ifupdown.
Unpacking ifupdown (from .../ifupdown_0.6.8ubuntu19_i386.deb) ...
Selecting previously deselected package initramfs-tools.
Unpacking initramfs-tools (from .../initramfs-tools_0.92bubuntu29_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 59: /sbin/vol_id: not found
Selecting previously deselected package iproute.
Unpacking iproute (from .../iproute_20080725-2_i386.deb) ...
Selecting previously deselected package iputils-ping.
Unpacking iputils-ping (from .../iputils-ping_3%3a20071127-1_i386.deb) ...
Selecting previously deselected package kbd.
Unpacking kbd (from .../kbd_1.14.1-4ubuntu4_i386.deb) ...
Selecting previously deselected package klibc-utils.
Unpacking klibc-utils (from .../klibc-utils_1.5.14-1~exp1ubuntu2_i386.deb) ...
Selecting previously deselected package klogd.
Unpacking klogd (from .../klogd_1.5-5ubuntu3_i386.deb) ...
Selecting previously deselected package laptop-detect.
Unpacking laptop-detect (from .../laptop-detect_0.13.7ubuntu1_i386.deb) ...
Selecting previously deselected package less.
Unpacking less (from .../archives/less_418-1_i386.deb) ...
Selecting previously deselected package libatm1.
Unpacking libatm1 (from .../libatm1_2.4.1-17.2_i386.deb) ...
Selecting previously deselected package libbz2-1.0.
Unpacking libbz2-1.0 (from .../libbz2-1.0_1.0.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package libc6-i686.
Unpacking libc6-i686 (from .../libc6-i686_2.9-4ubuntu6_i386.deb) ...
Selecting previously deselected package libcap2.
Unpacking libcap2 (from .../libcap2_2.11-2_i386.deb) ...
Selecting previously deselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.31-2_all.deb) ...
Selecting previously deselected package libcurl3-gnutls.
Unpacking libcurl3-gnutls (from .../libcurl3-gnutls_7.18.2-8ubuntu4_i386.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.12-4ubuntu1_i386.deb) ...
Selecting previously deselected package libdb4.6.
Unpacking libdb4.6 (from .../libdb4.6_4.6.21-12_i386.deb) ...
Selecting previously deselected package libdevmapper1.02.1.
Unpacking libdevmapper1.02.1 (from .../libdevmapper1.02.1_2%3a1.02.27-4ubuntu5_i386.deb) ...
Selecting previously deselected package libept0.
Unpacking libept0 (from .../libept0_0.5.26build1_i386.deb) ...
Selecting previously deselected package libfribidi0.
Unpacking libfribidi0 (from .../libfribidi0_0.10.9-1_i386.deb) ...
Selecting previously deselected package libgcrypt11.
Unpacking libgcrypt11 (from .../libgcrypt11_1.4.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package libgdbm3.
Unpacking libgdbm3 (from .../libgdbm3_1.8.3-4_i386.deb) ...
Selecting previously deselected package libgnutls26.
Unpacking libgnutls26 (from .../libgnutls26_2.4.2-6_i386.deb) ...
Selecting previously deselected package libgpg-error0.
Unpacking libgpg-error0 (from .../libgpg-error0_1.4-2ubuntu7_i386.deb) ...
Selecting previously deselected package libgpm2.
Unpacking libgpm2 (from .../libgpm2_1.20.4-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package libidn11.
Unpacking libidn11 (from .../libidn11_1.10-3_i386.deb) ...
Selecting previously deselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously deselected package libkeyutils1.
Unpacking libkeyutils1 (from .../libkeyutils1_1.2-9_i386.deb) ...
Selecting previously deselected package libklibc.
Unpacking libklibc (from .../libklibc_1.5.14-1~exp1ubuntu2_i386.deb) ...
Selecting previously deselected package libkrb53.
Unpacking libkrb53 (from .../libkrb53_1.6.dfsg.4~beta1-5ubuntu2_i386.deb) ...
Selecting previously deselected package libldap-2.4-2.
Unpacking libldap-2.4-2 (from .../libldap-2.4-2_2.4.15-1ubuntu3_i386.deb) ...
Selecting previously deselected package liblockfile1.
Unpacking liblockfile1 (from .../liblockfile1_1.08-3_i386.deb) ...
Selecting previously deselected package libmagic1.
Unpacking libmagic1 (from .../libmagic1_4.26-2ubuntu3_i386.deb) ...
Selecting previously deselected package libncursesw5.
Unpacking libncursesw5 (from .../libncursesw5_5.7+20090207-1ubuntu1_i386.deb) ...
Selecting previously deselected package libnewt0.52.
Unpacking libnewt0.52 (from .../libnewt0.52_0.52.2-11.3ubuntu3_i386.deb) ...
Selecting previously deselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.1.1-2ubuntu1_all.deb) ...
Selecting previously deselected package libpopt0.
Unpacking libpopt0 (from .../libpopt0_1.14-4_i386.deb) ...
Selecting previously deselected package libreadline5.
Unpacking libreadline5 (from .../libreadline5_5.2-4_i386.deb) ...
Selecting previously deselected package libsasl2-2.
Unpacking libsasl2-2 (from .../libsasl2-2_2.1.22.dfsg1-23ubuntu3_i386.deb) ...
Selecting previously deselected package libsasl2-modules.
Unpacking libsasl2-modules (from .../libsasl2-modules_2.1.22.dfsg1-23ubuntu3_i386.deb) ...
Selecting previously deselected package libsigc++-2.0-0c2a.
Unpacking libsigc++-2.0-0c2a (from .../libsigc++-2.0-0c2a_2.0.18-2_i386.deb) ...
Selecting previously deselected package libsqlite3-0.
Unpacking libsqlite3-0 (from .../libsqlite3-0_3.6.10-1_i386.deb) ...
Selecting previously deselected package libssl0.9.8.
Unpacking libssl0.9.8 (from .../libssl0.9.8_0.9.8g-15ubuntu3_i386.deb) ...
Selecting previously deselected package libtasn1-3.
Unpacking libtasn1-3 (from .../libtasn1-3_1.5-1_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package libusb-0.1-4.
Unpacking libusb-0.1-4 (from .../libusb-0.1-4_2%3a0.1.12-13_i386.deb) ...
Selecting previously deselected package libxapian15.
Unpacking libxapian15 (from .../libxapian15_1.0.7-4_i386.deb) ...
Selecting previously deselected package lockfile-progs.
Unpacking lockfile-progs (from .../lockfile-progs_0.1.11ubuntu2_i386.deb) ...
Selecting previously deselected package lsb-release.
Unpacking lsb-release (from .../lsb-release_3.2-20ubuntu4_all.deb) ...
Selecting previously deselected package mime-support.
Unpacking mime-support (from .../mime-support_3.44-1_all.deb) ...
Selecting previously deselected package module-init-tools.
Unpacking module-init-tools (from .../module-init-tools_3.7~pre9-2_i386.deb) ...
Selecting previously deselected package net-tools.
Unpacking net-tools (from .../net-tools_1.60-21ubuntu1_i386.deb) ...
Selecting previously deselected package netbase.
Unpacking netbase (from .../netbase_4.34ubuntu2_all.deb) ...
Selecting previously deselected package netcat.
Unpacking netcat (from .../netcat_1.10-38_all.deb) ...
Selecting previously deselected package netcat-traditional.
Unpacking netcat-traditional (from .../netcat-traditional_1.10-38_i386.deb) ...
Selecting previously deselected package ntpdate.
Unpacking ntpdate (from .../ntpdate_1%3a4.2.4p4+dfsg-7ubuntu5_i386.deb) ...
Selecting previously deselected package openssl.
Unpacking openssl (from .../openssl_0.9.8g-15ubuntu3_i386.deb) ...
Selecting previously deselected package perl.
Unpacking perl (from .../perl_5.10.0-19ubuntu1_i386.deb) ...
Selecting previously deselected package perl-modules.
Unpacking perl-modules (from .../perl-modules_5.10.0-19ubuntu1_all.deb) ...
Selecting previously deselected package python.
Unpacking python (from .../python_2.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package python2.6.
Unpacking python2.6 (from .../python2.6_2.6.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package readline-common.
Unpacking readline-common (from .../readline-common_5.2-4_all.deb) ...
Selecting previously deselected package sudo.
Unpacking sudo (from .../sudo_1.6.9p17-1ubuntu3_i386.deb) ...
Selecting previously deselected package sysklogd.
Unpacking sysklogd (from .../sysklogd_1.5-5ubuntu3_i386.deb) ...
Selecting previously deselected package tasksel.
Unpacking tasksel (from .../tasksel_2.73ubuntu18_all.deb) ...
Selecting previously deselected package tasksel-data.
Unpacking tasksel-data (from .../tasksel-data_2.73ubuntu18_all.deb) ...
Selecting previously deselected package ubuntu-keyring.
Unpacking ubuntu-keyring (from .../ubuntu-keyring_2008.03.04_all.deb) ...
Selecting previously deselected package ubuntu-minimal.
Unpacking ubuntu-minimal (from .../ubuntu-minimal_1.140_i386.deb) ...
Selecting previously deselected package udev.
Unpacking udev (from .../archives/udev_141-1_i386.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Selecting previously deselected package vim-common.
Unpacking vim-common (from .../vim-common_2%3a7.2.079-1ubuntu5_i386.deb) ...
Selecting previously deselected package vim-tiny.
Unpacking vim-tiny (from .../vim-tiny_2%3a7.2.079-1ubuntu5_i386.deb) ...
Selecting previously deselected package whiptail.
Unpacking whiptail (from .../whiptail_0.52.2-11.3ubuntu3_i386.deb) ...
Selecting previously deselected package xkb-data.
Unpacking xkb-data (from .../xkb-data_1.5-2ubuntu11_all.deb) ...
Setting up sudo (1.6.9p17-1ubuntu3) ...
No /etc/sudoers found... creating one for you.

Setting up gpgv (1.4.9-3ubuntu1) ...
Setting up module-init-tools (3.7~pre9-2) ...

Setting up libgdbm3 (1.8.3-4) ...

Setting up libtasn1-3 (1.5-1) ...

Setting up libpopt0 (1.14-4) ...

Setting up libusb-0.1-4 (2:0.1.12-13) ...

Setting up libgpg-error0 (1.4-2ubuntu7) ...

Setting up libssl0.9.8 (0.9.8g-15ubuntu3) ...

Setting up vim-common (2:7.2.079-1ubuntu5) ...

Setting up openssl (0.9.8g-15ubuntu3) ...

Setting up apt (0.7.20.2ubuntu6) ...

Setting up netbase (4.34ubuntu2) ...

Setting up libmagic1 (4.26-2ubuntu3) ...

Setting up libxapian15 (1.0.7-4) ...

Setting up dmidecode (2.9-1ubuntu1) ...
Setting up file (4.26-2ubuntu3) ...
Setting up libfribidi0 (0.10.9-1) ...

Setting up adduser (3.110ubuntu5) ...

Setting up libklibc (1.5.14-1~exp1ubuntu2) ...
Setting up libsqlite3-0 (3.6.10-1) ...

Setting up libkeyutils1 (1.2-9) ...

Setting up iproute (20080725-2) ...
Setting up libdevmapper1.02.1 (2:1.02.27-4ubuntu5) ...

Setting up libidn11 (1.10-3) ...

Setting up libatm1 (2.4.1-17.2) ...

Setting up klibc-utils (1.5.14-1~exp1ubuntu2) ...
Setting up libnewt0.52 (0.52.2-11.3ubuntu3) ...

Setting up libdb4.6 (4.6.21-12) ...
Setting up net-tools (1.60-21ubuntu1) ...
Setting up xkb-data (1.5-2ubuntu11) ...
Setting up libsigc++-2.0-0c2a (2.0.18-2) ...

Setting up netcat-traditional (1.10-3 ...

Setting up libgpm2 (1.20.4-3.1ubuntu1) ...

Setting up libept0 (0.5.26build1) ...

Setting up libncursesw5 (5.7+20090207-1ubuntu1) ...

Setting up eject (2.1.5+deb1+cvs20081104-5) ...
Setting up busybox-initramfs (1:1.10.2-2ubuntu7) ...
Setting up iputils-ping (3:20071127-1) ...
Setting up libbz2-1.0 (1.0.5-1ubuntu1) ...

Setting up libc6-i686 (2.9-4ubuntu6) ...

Setting up mime-support (3.44-1) ...

Setting up dhcp3-common (3.1.1-5ubuntu ...
Setting up apt-utils (0.7.20.2ubuntu6) ...

Setting up libkrb53 (1.6.dfsg.4~beta1-5ubuntu2) ...

Setting up cpio (2.9-15ubuntu1) ...

Setting up ca-certificates (20080809) ...
Updating certificates in /etc/ssl/certs....done.
Running hooks in /etc/ca-certificates/update.d....done.

Setting up vim-tiny (2:7.2.079-1ubuntu5) ...

Setting up less (418-1) ...

Setting up readline-common (5.2-4) ...

Setting up libcap2 (2.11-2) ...

Setting up netcat (1.10-3 ...
Setting up liblockfile1 (1.08-3) ...

Setting up laptop-detect (0.13.7ubuntu1) ...
Setting up libgcrypt11 (1.4.1-2ubuntu1) ...

Setting up bzip2 (1.0.5-1ubuntu1) ...

Setting up whiptail (0.52.2-11.3ubuntu3) ...
Setting up ifupdown (0.6.8ubuntu19) ...
ifupdown.postinst: Warning: No 'iface lo' definition found in /etc/network/interfaces
ifupdown.postinst: Warning: No 'auto lo' statement found in /etc/network/interfaces

Setting up dhcp3-client (3.1.1-5ubuntu ...

Setting up libreadline5 (5.2-4) ...

Setting up lockfile-progs (0.1.11ubuntu2) ...
Setting up libcwidget3 (0.5.12-4ubuntu1) ...

Setting up libgnutls26 (2.4.2-6) ...

Setting up aptitude (0.4.11.11-1ubuntu1) ...

Setting up ntpdate (1:4.2.4p4+dfsg-7ubuntu5) ...
Setting up python2.6 (2.6.2-0ubuntu1) ...

Setting up python (2.6.2-0ubuntu1) ...

Setting up lsb-release (3.2-20ubuntu4) ...

Setting up libsasl2-modules (2.1.22.dfsg1-23ubuntu3) ...
Setting up libsasl2-2 (2.1.22.dfsg1-23ubuntu3) ...

Setting up console-terminus (4.26-2.1) ...
Setting up sysklogd (1.5-5ubuntu3) ...
 * Starting system log daemon...

Warning: Fake start-stop-daemon called, doing nothing
   ...done.

Setting up libldap-2.4-2 (2.4.15-1ubuntu3) ...

Setting up klogd (1.5-5ubuntu3) ...
 * Starting kernel log daemon...

Warning: Fake start-stop-daemon called, doing nothing

Warning: Fake start-stop-daemon called, doing nothing
   ...done.

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up libcurl3-gnutls (7.18.2-8ubuntu4) ...

Setting up perl-modules (5.10.0-19ubuntu1) ...
Setting up console-setup (1.28ubuntu ...
 * Setting up console font and keymap...
   ...done.
update-initramfs: deferring update (trigger activated)

Setting up tasksel-data (2.73ubuntu1 ...
Setting up gnupg (1.4.9-3ubuntu1) ...
Setting up kbd (1.14.1-4ubuntu4) ...
 Removing any system startup links for /etc/init.d/console-screen.kbd.sh ...
update-initramfs: deferring update (trigger activated)

Setting up ubuntu-keyring (2008.03.04) ...
gpg: /etc/apt/trustdb.gpg: trustdb created
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 17 new signatures
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: Total number processed: 2
gpg:               imported: 1
gpg:         new signatures: 17
gpg: no ultimately trusted keys found
gpg: keyring `/usr/share/keyrings/ubuntu-archive-removed-keys.gpg' created

Setting up dmsetup (2:1.02.27-4ubuntu5) ...
update-initramfs: deferring update (trigger activated)

Setting up perl (5.10.0-19ubuntu1) ...

Setting up udev (141-1) ...
 * Stopping kernel event manager...

Warning: Fake start-stop-daemon called, doing nothing
   ...done.
 * Starting kernel event manager...

Warning: Fake start-stop-daemon called, doing nothing
   ...done.
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Setting up libio-string-perl (1.08-2) ...
Setting up libclass-accessor-perl (0.31-2) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up tasksel (2.73ubuntu1 ...

Setting up libparse-debianchangelog-perl (1.1.1-2ubuntu1) ...
Setting up ubuntu-minimal (1.140) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
```



after seeing these dependency problems i decided to dl the packages it says it is depending on.

i proceeded to install:
-dpkg-awk
- libc6-dbg
-libc6-dbg-armel-cross (along with other required packages for use)
-libc6-amd64 and libc6-dev-amd64 (since i have amd i figure this would be needed. but i have no clue what i am doing.
-libpam-modules (reinstalled)
-coreutils(reinstall)
-lzma (reinstall)
-libgcc1 (everything that appears in search)
-findutils(re)
-debconf-i18n(re)
-debconf-english
-libselinux1(re)
-libacl1(re) (and dev)
-libncurses5 (and dev and dbg)

restarting comp now.

---

### Post by SebSmith on 2010-12-02
none of that worked... ok so upon more exploring i checked out daemon.log. i think i found the problem...

```
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]: <info> NetworkManager (version 0.8.1) is starting...
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]: <info> trying to start the modem manager...
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: init!
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: update_system_hostname
Dec  2 01:10:20 sebastian-laptop avahi-daemon[850]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Dec  2 01:10:20 sebastian-laptop avahi-daemon[850]: Successfully dropped root privileges.
Dec  2 01:10:20 sebastian-laptop avahi-daemon[850]: avahi-daemon 0.6.27 starting up.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPluginIfupdown: management mode: unmanaged
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/net/eth0, iface: eth0)
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0)
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: end _init.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    Ifupdown: get unmanaged devices count: 0
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: (161500496) ... get_connections.
Dec  2 01:10:20 sebastian-laptop NetworkManager[843]:    SCPlugin-Ifupdown: (161500496) ... get_connections (managed=false): return empty list.
Dec  2 01:10:21 sebastian-laptop avahi-daemon[850]: Successfully called chroot().
Dec  2 01:10:21 sebastian-laptop avahi-daemon[850]: Successfully dropped remaining capabilities.
Dec  2 01:10:21 sebastian-laptop modem-manager: ModemManager (version 0.4) starting...
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]:    Ifupdown: get unmanaged devices count: 0
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Dec  2 01:10:21 sebastian-laptop avahi-daemon[850]: No service file found in /etc/avahi/services.
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> Networking is enabled by state file
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): carrier is OFF
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Nokia
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin AnyData
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Ericsson MBM
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin MotoC
Dec  2 01:10:21 sebastian-laptop avahi-daemon[850]: Network interface enumeration completed.
Dec  2 01:10:21 sebastian-laptop avahi-daemon[850]: Registering HINFO record with values 'I686'/'LINUX'.
Dec  2 01:10:21 sebastian-laptop avahi-daemon[850]: Server startup complete. Host name is sebastian-laptop.local. Local service cookie is 3880833616.
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Option High-Speed
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Gobi
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin SimTech
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Novatel
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Option
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Longcheer
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin ZTE
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): now managed
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): bringing up device.
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Generic
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Sierra
Dec  2 01:10:21 sebastian-laptop modem-manager: Loaded plugin Huawei
Dec  2 01:10:21 sebastian-laptop modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Dec  2 01:10:21 sebastian-laptop modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Dec  2 01:10:21 sebastian-laptop modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Dec  2 01:10:21 sebastian-laptop modem-manager: (tty/ttyS0): could not get port's parent device
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): preparing device.
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (eth0): deactivating device (reason: 2).
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/net/eth0
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (wlan0): now managed
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Dec  2 01:10:21 sebastian-laptop NetworkManager[843]: <info> (wlan0): bringing up device.
Dec  2 01:10:21 sebastian-laptop gdm-binary[902]: WARNING: Unable to find users: no seat-id found
Dec  2 01:10:21 sebastian-laptop init: apport pre-start process (988) terminated with status 1
Dec  2 01:10:22 sebastian-laptop acpid: starting up with proc fs
Dec  2 01:10:22 sebastian-laptop acpid: 36 rules loaded
Dec  2 01:10:22 sebastian-laptop acpid: waiting for events: event logging is off
Dec  2 01:10:22 sebastian-laptop init: apport post-stop process (1018) terminated with status 1
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> (wlan0): preparing device.
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> (wlan0): deactivating device (reason: 2).
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> modem-manager is now available
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> Trying to start the supplicant...
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant manager state:  down -> idle
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Dec  2 01:10:22 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant interface state:  starting -> ready
Dec  2 01:10:22 sebastian-laptop acpid: client connected from 1088[0:0]
Dec  2 01:10:22 sebastian-laptop acpid: 1 client rule loaded
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Successfully called chroot.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Successfully dropped privileges.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Successfully limited resources.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Running.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Canary thread running.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Watchdog thread running.
Dec  2 01:10:23 sebastian-laptop polkitd[1181]: started daemon version 0.96 using authority implementation `local' version `0.96'
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Successfully made thread 1168 of process 1168 (n/a) owned by '105' high priority at nice level -11.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Supervising 1 threads of 1 processes of 1 users.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Successfully made thread 1222 of process 1168 (n/a) owned by '105' RT at priority 5.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Supervising 2 threads of 1 processes of 1 users.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Successfully made thread 1223 of process 1168 (n/a) owned by '105' RT at priority 5.
Dec  2 01:10:23 sebastian-laptop rtkit-daemon[1173]: Supervising 3 threads of 1 processes of 1 users.
Dec  2 01:10:24 sebastian-laptop init: plymouth-stop pre-start process (1275) terminated with status 1
Dec  2 01:10:24 sebastian-laptop gdm-simple-greeter[1146]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Dec  2 01:10:24 sebastian-laptop gdm-simple-greeter[1146]: WARNING: Unable to lookup user name sebastia: Success
Dec  2 01:10:25 sebastian-laptop gdm-session-worker[1155]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Dec  2 01:10:28 sebastian-laptop NetworkManager[843]: <error> [1291270228.660042] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec  2 01:10:28 sebastian-laptop NetworkManager[843]: <error> [1291270228.698874] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec  2 01:10:29 sebastian-laptop rtkit-daemon[1173]: Successfully made thread 1451 of process 1451 (n/a) owned by '1000' high priority at nice level -11.
Dec  2 01:10:29 sebastian-laptop rtkit-daemon[1173]: Supervising 4 threads of 2 processes of 2 users.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) starting connection 'Auto flamingonet'
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0/wireless): access point 'Auto flamingonet' has security, but secrets are required.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0/wireless): connection 'Auto flamingonet' has security, and secrets exist.  No new secrets needed.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Config: added 'ssid' value 'flamingonet'
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Config: added 'scan_ssid' value '1'
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Config: added 'psk' value '<omitted>'
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> Config: set interface ap_scan to 1
Dec  2 01:10:32 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Dec  2 01:10:33 sebastian-laptop wpa_supplicant[1041]: Trying to associate with 00:26:f2:9c:d2:9c (SSID='flamingonet' freq=2412 MHz)
Dec  2 01:10:33 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  2 01:10:33 sebastian-laptop wpa_supplicant[1041]: Associated with 00:26:f2:9c:d2:9c
Dec  2 01:10:33 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant connection state:  associating -> associated
Dec  2 01:10:33 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  2 01:10:33 sebastian-laptop wpa_supplicant[1041]: WPA: Key negotiation completed with 00:26:f2:9c:d2:9c [PTK=TKIP GTK=TKIP]
Dec  2 01:10:33 sebastian-laptop wpa_supplicant[1041]: CTRL-EVENT-CONNECTED - Connection to 00:26:f2:9c:d2:9c completed (auth) [id=0 id_str=]
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'flamingonet'.
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> dhclient started with pid 1579
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec  2 01:10:34 sebastian-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec  2 01:10:34 sebastian-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec  2 01:10:34 sebastian-laptop dhclient: All rights reserved.
Dec  2 01:10:34 sebastian-laptop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec  2 01:10:34 sebastian-laptop dhclient: 
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec  2 01:10:34 sebastian-laptop dhclient: Listening on LPF/wlan0/00:14:a4:3c:d6:a6
Dec  2 01:10:34 sebastian-laptop dhclient: Sending on   LPF/wlan0/00:14:a4:3c:d6:a6
Dec  2 01:10:34 sebastian-laptop dhclient: Sending on   Socket/fallback
Dec  2 01:10:34 sebastian-laptop dhclient: DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67
Dec  2 01:10:34 sebastian-laptop dhclient: DHCPACK of 192.168.1.66 from 192.168.1.1
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info>   address 192.168.1.66
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info>   prefix 24 (255.255.255.0)
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info>   gateway 192.168.1.1
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info>   nameserver '192.168.1.1'
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  2 01:10:34 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec  2 01:10:34 sebastian-laptop avahi-daemon[850]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.66.
Dec  2 01:10:34 sebastian-laptop avahi-daemon[850]: New relevant interface wlan0.IPv4 for mDNS.
Dec  2 01:10:34 sebastian-laptop avahi-daemon[850]: Registering new address record for 192.168.1.66 on wlan0.IPv4.
Dec  2 01:10:34 sebastian-laptop dhclient: bound to 192.168.1.66 -- renewal in 36351 seconds.
Dec  2 01:10:35 sebastian-laptop NetworkManager[843]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Dec  2 01:10:35 sebastian-laptop NetworkManager[843]: <info> Policy set 'Auto flamingonet' (wlan0) as default for IPv4 routing and DNS.
Dec  2 01:10:35 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) successful, device activated.
Dec  2 01:10:35 sebastian-laptop NetworkManager[843]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec  2 01:10:35 sebastian-laptop avahi-daemon[850]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::214:a4ff:fe3c:d6a6.
Dec  2 01:10:35 sebastian-laptop avahi-daemon[850]: New relevant interface wlan0.IPv6 for mDNS.
Dec  2 01:10:35 sebastian-laptop avahi-daemon[850]: Registering new address record for fe80::214:a4ff:fe3c:d6a6 on wlan0.*.
Dec  2 01:10:36 sebastian-laptop ntpdate[1642]: adjust time server 91.189.94.4 offset -0.243913 sec
Dec  2 01:10:46 sebastian-laptop gnome-session[1364]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-user-share/gnome-user-share" (No such file or directory)
```


the time frames listed is during the boot up. im clueless to this or what it means or how to fix it

---

### Post by oldos2er on 2010-12-02
Are you able to boot into recovery mode? If so, I would try these commands one at a time.

[B]apt-get clean && apt-get autoclean
apt-get install -f
dpkg --configure -a[/B]

Also try installing gnome-user-share, since it seems to be looking for it.

---

### Post by SebSmith on 2010-12-02
woooooow deleting network manager was a bad idea... i was done for until i figured out how to make an eth0 connect. ok so those commands didnt work, but i got user share. problem persists


syslog

Dec  2 19:11:06 sebastian-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec  2 19:11:06 sebastian-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="764" x-info="http://www.rsyslog.com"] (re)start
Dec  2 19:11:06 sebastian-laptop rsyslogd: rsyslogd's groupid changed to 102
Dec  2 19:11:06 sebastian-laptop rsyslogd: rsyslogd's userid changed to 101
Dec  2 19:11:06 sebastian-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Linux version 2.6.35-23-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 (Ubuntu 2.6.35-23.41-generic 2.6.35.7)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005fef0000 (usable)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 000000005fef0000 - 000000005fefb000 (ACPI data)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 000000005fefb000 - 000000005ff00000 (ACPI NVS)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 000000005ff00000 - 0000000060000000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] DMI present.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] last_pfn = 0x5fef0 max_arch_pfn = 0x100000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] MTRR default type: uncachable
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   00000-9FFFF write-back
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   C0000-CFFFF write-protect
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   D0000-DFFFF uncachable
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   E0000-E3FFF write-back
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   E4000-FFFFF write-protect
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   1 base 0040000000 mask FFE0000000 write-back
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   2 disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   3 disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   4 disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   5 disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   6 disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   7 disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] modified physical RAM map:
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000005fef0000 (usable)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 000000005fef0000 - 000000005fefb000 (ACPI data)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 000000005fefb000 - 000000005ff00000 (ACPI NVS)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 000000005ff00000 - 0000000060000000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] found SMP MP-table at [c00f6ae0] f6ae0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] RAMDISK: 375ae000 - 37ff0000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Allocated new RAMDISK: 009a5000 - 013e6ea4
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Move RAMDISK from 00000000375ae000 - 0000000037fefea3 to 009a5000 - 013e6ea3
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: RSDP 000f6ab0 00014 (v00 PTLTD )
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: RSDT 5fef4908 00034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: FACP 5fefadff 00074 (v01 ATI    Firanha  06040000 ATI  000F4240)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: DSDT 5fef493c 064C3 (v01    ATI    SB400 06040000 MSFT 0100000E)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: FACS 5fefbfc0 00040
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: SSDT 5fefae73 000F7 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: APIC 5fefaf6a 0005A (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: MCFG 5fefafc4 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] 646MB HIGHMEM available.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] 887MB LOWMEM available.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Zone PFN ranges:
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0005fef0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Movable zone start PFN for each node
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0005fef0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] On node 0 totalpages: 392832
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c13e8020
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   DMA zone: 3952 pages, LIFO batch:0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   HighMem zone: 1294 pages used for memmap
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   HighMem zone: 164324 pages, LIFO batch:31
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Using APIC driver default
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] SB4X0 revision 0x11
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Ignoring ACPI timer override.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] nr_irqs_gsi: 40
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:80000000)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36416 r0 d20928 u4194304
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389762
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=/dev/sda5 ro quiet splash
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Initializing CPU#0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] allocated 7858860 bytes of page_cgroup
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Subtract (49 early reservations)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #3 [00009a1000 - 00009a40fc]             BRK
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #4 [00000f6af0 - 0000100000]   BIOS reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #5 [00000f6ae0 - 00000f6af0]    MP-table mpf
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #6 [000009f800 - 000009fd70]   BIOS reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #7 [000009fed8 - 00000f6ae0]   BIOS reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #8 [000009fd70 - 000009fed8]    MP-table mpc
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #12 [00009a5000 - 00013e7000]     NEW RAMDISK
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #13 [00013e7000 - 00013e8000]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #14 [00013e8000 - 0001fe8000]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #15 [0001fe8000 - 0001fe8004]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #16 [0001fe8040 - 0001fe8100]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #17 [0001fe8100 - 0001fe8154]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #18 [0001fe8180 - 0001feb180]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #19 [0001feb180 - 0001feb1c0]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #20 [0001feb1c0 - 0001fee1c0]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #21 [0001fee1c0 - 0001fee1e7]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #22 [0001fee200 - 0001fee388]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #23 [0001fee3c0 - 0001fee400]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #24 [0001fee400 - 0001fee440]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #25 [0001fee440 - 0001fee480]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #26 [0001fee480 - 0001fee4c0]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #27 [0001fee4c0 - 0001fee500]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #28 [0001fee500 - 0001fee540]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #29 [0001fee540 - 0001fee580]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #30 [0001fee580 - 0001fee5c0]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #31 [0001fee5c0 - 0001fee600]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #32 [0001fee600 - 0001fee640]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #33 [0001fee640 - 0001fee680]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #34 [0001fee680 - 0001fee690]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #35 [0001fee6c0 - 0001fee6d0]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #36 [0001fee700 - 0001fee74a]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #37 [0001fee780 - 0001fee7ca]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #38 [0002000000 - 000200e000]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #39 [0001ff0800 - 0001ff0804]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #40 [0001ff0840 - 0001ff0844]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #41 [0001ff0880 - 0001ff0884]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #42 [0001ff08c0 - 0001ff08c4]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #43 [0001ff0900 - 0001ff09b0]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #44 [0001ff09c0 - 0001ff0a68]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #45 [0001ff0a80 - 0001ff4a80]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #46 [000200e000 - 000208e000]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #47 [000208e000 - 00020ce000]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]   #48 [00020ce000 - 000284caac]         BOOTMEM
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0005fef0)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Memory: 1531104k/1571776k available (4930k kernel code, 40224k reserved, 2334k data, 684k init, 662472k highmem)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] virtual kernel memory layout:
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]       .data : 0xc05d0bee - 0xc0818628   (2334 kB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d0bee   (4930 kB)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] console [tty0] enabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Dec  2 19:11:06 sebastian-laptop kernel: [    0.000000] Detected 2000.172 MHz processor.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.34 BogoMIPS (lpj=8000688)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004045] Security Framework initialized
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004076] AppArmor: AppArmor initialized
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004079] Yama: becoming mindful.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004156] Mount-cache hash table entries: 512
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004319] Initializing cgroup subsys ns
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004324] Initializing cgroup subsys cpuacct
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004330] Initializing cgroup subsys memory
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004341] Initializing cgroup subsys devices
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004345] Initializing cgroup subsys freezer
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004349] Initializing cgroup subsys net_cls
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004381] mce: CPU supports 5 MCE banks
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004402] Performance Events: AMD PMU driver.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004412] ... version:                0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004414] ... bit width:              48
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004417] ... generic registers:      4
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004420] ... value mask:             0000ffffffffffff
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004423] ... max period:             00007fffffffffff
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004426] ... fixed-purpose events:   0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.004429] ... event mask:             000000000000000f
Dec  2 19:11:06 sebastian-laptop kernel: [    0.005422] SMP alternatives: switching to UP code
Dec  2 19:11:06 sebastian-laptop kernel: [    0.015230] Freeing SMP alternatives: 24k freed
Dec  2 19:11:06 sebastian-laptop kernel: [    0.015247] ACPI: Core revision 20100428
Dec  2 19:11:06 sebastian-laptop kernel: [    0.024012] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec  2 19:11:06 sebastian-laptop kernel: [    0.024020] ftrace: allocating 21766 entries in 43 pages
Dec  2 19:11:06 sebastian-laptop kernel: [    0.028108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec  2 19:11:06 sebastian-laptop kernel: [    0.028459] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Dec  2 19:11:06 sebastian-laptop kernel: [    0.068956] CPU0: AMD Turion(tm) 64 Mobile Technology ML-37 stepping 02
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] Brought up 1 CPUs
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] Total of 1 processors activated (4000.34 BogoMIPS).
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] devtmpfs: initialized
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] regulator: core version 0.5
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] Time:  0:10:40  Date: 12/03/10
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] NET: Registered protocol family 16
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] EISA bus registered
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] node 0 link 0: io port [1000, fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] TOM: 0000000060000000 aka 1536M
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] node 0 link 0: mmio [a0000, bffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] node 0 link 0: mmio [60000000, fff8ffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] bus: [00, ff] on node 0 link 0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] bus: 00 index 0 [io  0x0000-0xffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] bus: 00 index 2 [mem 0x60000000-0xffffffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] ACPI: bus type pci registered
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] PCI: MMCONFIG for domain 0000 [bus 00-06] at [mem 0xe0000000-0xe06fffff] (base 0xe0000000)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] PCI: MMCONFIG at [mem 0xe0000000-0xe06fffff] reserved in E820
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] PCI: Using MMCONFIG for extended config space
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] PCI: Using configuration type 1 for base access
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] bio: create slab <bio-0> at 0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.072000] ACPI: EC: Look up EC in DSDT
Dec  2 19:11:06 sebastian-laptop kernel: [    0.092253] ACPI: Interpreter enabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.092253] ACPI: (supports S0 S3 S4 S5)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.092253] ACPI: Using IOAPIC for interrupt routing
Dec  2 19:11:06 sebastian-laptop kernel: [    0.100316] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
Dec  2 19:11:06 sebastian-laptop kernel: [    0.101286] ACPI: ACPI Dock Station Driver: 2 docks/bays found
Dec  2 19:11:06 sebastian-laptop kernel: [    0.101291] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Dec  2 19:11:06 sebastian-laptop kernel: [    0.102199] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104023] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104027] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104030] pci_root PNP0A03:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104033] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104036] pci_root PNP0A03:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104039] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104042] pci_root PNP0A03:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104045] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104048] pci_root PNP0A03:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104052] pci_root PNP0A03:00: host bridge window [mem 0x60000000-0xffffffff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104055] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104058] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104122] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104126] pci 0000:00:02.0: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104168] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104171] pci 0000:00:06.0: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104230] pci 0000:00:13.0: reg 10: [mem 0xc0000000-0xc0000fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104332] pci 0000:00:13.1: reg 10: [mem 0xc0001000-0xc0001fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104441] pci 0000:00:13.2: reg 10: [mem 0xc0002000-0xc0002fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104512] pci 0000:00:13.2: supports D1 D2
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104514] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104520] pci 0000:00:13.2: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104568] pci 0000:00:14.0: reg 10: [io  0x8400-0x840f]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104577] pci 0000:00:14.0: reg 14: [mem 0xc0003000-0xc00033ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104614] HPET not enabled in BIOS. You might try hpet=force boot option
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104673] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104682] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104691] pci 0000:00:14.1: reg 18: [io  0x0170-0x0177]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104700] pci 0000:00:14.1: reg 1c: [io  0x0374-0x0377]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104709] pci 0000:00:14.1: reg 20: [io  0x8410-0x841f]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104895] pci 0000:00:14.5: reg 10: [mem 0xc0003400-0xc00034ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.104994] pci 0000:00:14.6: reg 10: [mem 0xc0003800-0xc00038ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105147] PCI: peer root bus 00 res updated from pci conf
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105190] pci 0000:01:00.0: reg 10: [mem 0xc8000000-0xcfffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105196] pci 0000:01:00.0: reg 14: [io  0x9000-0x90ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105202] pci 0000:01:00.0: reg 18: [mem 0xc0100000-0xc010ffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105217] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105235] pci 0000:01:00.0: supports D1 D2
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105246] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105255] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105259] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105263] pci 0000:00:02.0:   bridge window [mem 0xc0100000-0xc01fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105267] pci 0000:00:02.0:   bridge window [mem 0xc8000000-0xcfffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105331] pci 0000:05:00.0: reg 10: [mem 0xc0200000-0xc020ffff 64bit]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105401] pci 0000:05:00.0: PME# supported from D3hot D3cold
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105406] pci 0000:05:00.0: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105422] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105431] pci 0000:00:06.0: PCI bridge to [bus 05-05]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105436] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105439] pci 0000:00:06.0:   bridge window [mem 0xc0200000-0xc02fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105443] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105488] pci 0000:06:02.0: reg 10: [mem 0xc0304000-0xc0305fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105600] pci 0000:06:09.0: reg 10: [mem 0xc0308000-0xc0308fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105632] pci 0000:06:09.0: supports D1 D2
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105635] pci 0000:06:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105641] pci 0000:06:09.0: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105692] pci 0000:06:09.2: reg 10: [mem 0xc0309000-0xc03097ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105703] pci 0000:06:09.2: reg 14: [mem 0xc0300000-0xc0303fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105777] pci 0000:06:09.2: supports D1 D2
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105780] pci 0000:06:09.2: PME# supported from D0 D1 D2 D3hot
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105786] pci 0000:06:09.2: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105835] pci 0000:06:09.3: reg 10: [mem 0xc0306000-0xc0307fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105914] pci 0000:06:09.3: supports D1 D2
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105916] pci 0000:06:09.3: PME# supported from D0 D1 D2 D3hot
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105922] pci 0000:06:09.3: PME# disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105985] pci 0000:00:14.4: PCI bridge to [bus 06-07] (subtractive decode)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.105994] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106000] pci 0000:00:14.4:   bridge window [mem 0xc0300000-0xc03fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106006] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106009] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106012] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106015] pci 0000:00:14.4:   bridge window [mem 0x60000000-0xffffffff] (subtractive decode)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106075] pci_bus 0000:07: [bus 07-0a] partially hidden behind transparent bridge 0000:06 [bus 06-07]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106092] pci_bus 0000:00: on NUMA node 0
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106277] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.106343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.109987] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110080] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110171] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110262] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110353] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110448] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110539] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110630] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110670] HEST: Table is not found!
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110747] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110752] vgaarb: loaded
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110918] SCSI subsystem initialized
Dec  2 19:11:06 sebastian-laptop kernel: [    0.110959] libata version 3.00 loaded.
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111013] usbcore: registered new interface driver usbfs
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111026] usbcore: registered new interface driver hub
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111051] usbcore: registered new device driver usb
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111184] ACPI: WMI: Mapper loaded
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111186] PCI: Using ACPI for IRQ routing
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111189] PCI: pci_cache_line_size set to 64 bytes
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111280] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111283] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111285] reserve RAM buffer: 000000005fef0000 - 000000005fffffff 
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111379] NetLabel: Initializing
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111381] NetLabel:  domain hash size = 128
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111383] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111396] NetLabel:  unlabeled traffic allowed by default
Dec  2 19:11:06 sebastian-laptop kernel: [    0.111450] Switching to clocksource tsc
Dec  2 19:11:06 sebastian-laptop kernel: [    0.118860] AppArmor: AppArmor Filesystem Enabled
Dec  2 19:11:06 sebastian-laptop kernel: [    0.118881] pnp: PnP ACPI init
Dec  2 19:11:06 sebastian-laptop kernel: [    0.118902] ACPI: bus type pnp registered
Dec  2 19:11:06 sebastian-laptop kernel: [    0.333564] pnp 00:08: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335287] pnp: PnP ACPI: found 12 devices
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335289] ACPI: ACPI bus type pnp unregistered
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335293] PnPBIOS: Disabled by ACPI PNP
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335307] system 00:07: [io  0x1080] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335310] system 00:07: [io  0x087f] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335313] system 00:07: [io  0x0200-0x020f] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335316] system 00:07: [io  0x040b] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335319] system 00:07: [io  0x04d0-0x04d1] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335322] system 00:07: [io  0x04d6] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335325] system 00:07: [io  0x0530-0x0537] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335328] system 00:07: [io  0x0c00-0x0c01] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335331] system 00:07: [io  0x0c14] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335334] system 00:07: [io  0x0c50-0x0c52] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335337] system 00:07: [io  0x0c6c] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335340] system 00:07: [io  0x0c6f] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335343] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335346] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335349] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335352] system 00:07: [io  0x8000-0x805f] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335356] system 00:07: [io  0x0f40-0x0f47] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335359] system 00:07: [io  0x0280-0x0293] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335363] system 00:07: [mem 0xe0000000-0xe00000ff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335367] system 00:07: [mem 0xe0010000-0xe0010fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335370] system 00:07: [mem 0xe0030000-0xe0030fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335373] system 00:07: [mem 0xe0098000-0xe009afff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335377] system 00:07: [mem 0xe00a0000-0xe00a1fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335380] system 00:07: [mem 0xe00a3000-0xe00a6fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335383] system 00:07: [mem 0xe0100000-0xe0100fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335387] system 00:07: [mem 0xe0500000-0xe0500fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335390] system 00:07: [mem 0xe0610000-0xe0617fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335399] system 00:07: [mem 0xe0648000-0xe064bfff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335402] system 00:07: [mem 0xfee00400-0xfee00fff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335408] system 00:08: [mem 0x000e0000-0x000fffff] could not be reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.335412] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371483] pci 0000:00:14.4: BAR 15: assigned [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371488] pci 0000:00:14.4: BAR 13: assigned [io  0x2000-0x2fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371491] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371495] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371498] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371503] pci 0000:00:02.0:   bridge window [mem 0xc0100000-0xc01fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371507] pci 0000:00:02.0:   bridge window [mem 0xc8000000-0xcfffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371511] pci 0000:00:06.0: PCI bridge to [bus 05-05]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371513] pci 0000:00:06.0:   bridge window [io  disabled]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371517] pci 0000:00:06.0:   bridge window [mem 0xc0200000-0xc02fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371520] pci 0000:00:06.0:   bridge window [mem pref disabled]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371525] pci 0000:06:09.0: BAR 15: assigned [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371529] pci 0000:06:09.0: BAR 16: assigned [mem 0x64000000-0x67ffffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371532] pci 0000:06:09.0: BAR 13: assigned [io  0x2000-0x20ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371535] pci 0000:06:09.0: BAR 14: assigned [io  0x2400-0x24ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371538] pci 0000:06:09.0: CardBus bridge to [bus 07-0a]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371541] pci 0000:06:09.0:   bridge window [io  0x2000-0x20ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371547] pci 0000:06:09.0:   bridge window [io  0x2400-0x24ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371554] pci 0000:06:09.0:   bridge window [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371560] pci 0000:06:09.0:   bridge window [mem 0x64000000-0x67ffffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371567] pci 0000:00:14.4: PCI bridge to [bus 06-07]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371571] pci 0000:00:14.4:   bridge window [io  0x2000-0x2fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371578] pci 0000:00:14.4:   bridge window [mem 0xc0300000-0xc03fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371584] pci 0000:00:14.4:   bridge window [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371600] pci 0000:00:02.0: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371606] pci 0000:00:06.0: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371623] pci 0000:06:09.0: enabling device (0004 -> 0007)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371631]   alloc irq_desc for 23 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371633]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371639] pci 0000:06:09.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371647] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371650] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371653] pci_bus 0000:00: resource 6 [mem 0x60000000-0xffffffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371656] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371658] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371661] pci_bus 0000:01: resource 2 [mem 0xc8000000-0xcfffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371664] pci_bus 0000:05: resource 1 [mem 0xc0200000-0xc02fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371667] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371670] pci_bus 0000:06: resource 1 [mem 0xc0300000-0xc03fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371673] pci_bus 0000:06: resource 2 [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371675] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371678] pci_bus 0000:06: resource 5 [mem 0x000a0000-0x000bffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371681] pci_bus 0000:06: resource 6 [mem 0x60000000-0xffffffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371683] pci_bus 0000:07: resource 0 [io  0x2000-0x20ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371686] pci_bus 0000:07: resource 1 [io  0x2400-0x24ff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371689] pci_bus 0000:07: resource 2 [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371692] pci_bus 0000:07: resource 3 [mem 0x64000000-0x67ffffff]
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371734] NET: Registered protocol family 2
Dec  2 19:11:06 sebastian-laptop kernel: [    0.371798] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.372141] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.373222] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.373825] TCP: Hash tables configured (established 131072 bind 65536)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.373827] TCP reno registered
Dec  2 19:11:06 sebastian-laptop kernel: [    0.373831] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.373855] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    0.373966] NET: Registered protocol family 1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.028581] pci 0000:01:00.0: Boot video device
Dec  2 19:11:06 sebastian-laptop kernel: [    1.028603] PCI: CLS 32 bytes, default 64
Dec  2 19:11:06 sebastian-laptop kernel: [    1.028818] cpufreq-nforce2: No nForce2 chipset.
Dec  2 19:11:06 sebastian-laptop kernel: [    1.028851] Scanning for low memory corruption every 60 seconds
Dec  2 19:11:06 sebastian-laptop kernel: [    1.029039] audit: initializing netlink socket (disabled)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.029049] type=2000 audit(1291335041.028:1): initialized
Dec  2 19:11:06 sebastian-laptop kernel: [    1.040287] Trying to unpack rootfs image as initramfs...
Dec  2 19:11:06 sebastian-laptop kernel: [    1.052738] highmem bounce pool size: 64 pages
Dec  2 19:11:06 sebastian-laptop kernel: [    1.052745] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec  2 19:11:06 sebastian-laptop kernel: [    1.057935] VFS: Disk quotas dquot_6.5.2
Dec  2 19:11:06 sebastian-laptop kernel: [    1.057999] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.064650] fuse init (API version 7.14)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.064760] msgmni has been set to 1696
Dec  2 19:11:06 sebastian-laptop kernel: [    1.068960] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.068964] io scheduler noop registered
Dec  2 19:11:06 sebastian-laptop kernel: [    1.068966] io scheduler deadline registered
Dec  2 19:11:06 sebastian-laptop kernel: [    1.068981] io scheduler cfq registered (default)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069100] pcieport 0000:00:02.0: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069124]   alloc irq_desc for 40 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069126]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069135] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069197] pcieport 0000:00:06.0: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069218]   alloc irq_desc for 41 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069220]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069224] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069295] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069303] aer 0000:00:06.0:pcie02: AER service couldn't init device: no _OSC support
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069324] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  2 19:11:06 sebastian-laptop kernel: [    1.069351] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec  2 19:11:06 sebastian-laptop kernel: [    1.070995] ACPI: AC Adapter [ACAD] (off-line)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.071070] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072388] ACPI: Lid Switch [LID]
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072439] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072444] ACPI: Power Button [PWRB]
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072494] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072498] ACPI: Sleep Button [SLPB]
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072573] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072576] ACPI: Power Button [PWRF]
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072724] ACPI: acpi_idle registered with cpuidle
Dec  2 19:11:06 sebastian-laptop kernel: [    1.072754] Marking TSC unstable due to TSC halts in idle
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078075] thermal LNXTHERM:01: registered as thermal_zone0
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078083] ACPI: Thermal Zone [THRM] (59 C)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078153] ERST: Table is not found!
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078313] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078456] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078581] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
Dec  2 19:11:06 sebastian-laptop kernel: [    1.078939] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  2 19:11:06 sebastian-laptop kernel: [    1.079013]   alloc irq_desc for 17 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.079016]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.079023] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  2 19:11:06 sebastian-laptop kernel: [    1.079030] serial 0000:00:14.6: PCI INT B disabled
Dec  2 19:11:06 sebastian-laptop kernel: [    1.080150] brd: module loaded
Dec  2 19:11:06 sebastian-laptop kernel: [    1.080686] loop: module loaded
Dec  2 19:11:06 sebastian-laptop kernel: [    1.084805] Switching to clocksource acpi_pm
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085035]   alloc irq_desc for 16 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085038]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085045] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085101] pata_acpi 0000:00:14.1: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085481] Fixed MDIO Bus: probed
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085519] PPP generic driver version 2.4.2
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085574] tun: Universal TUN/TAP device driver, 1.6
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085576] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085659] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085677]   alloc irq_desc for 19 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085679]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085683] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085707] ehci_hcd 0000:00:13.2: EHCI Host Controller
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085745] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085810] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085921] ACPI: Battery Slot [BAT1] (battery absent)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.085933] isapnp: Scanning for PnP cards...
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092219] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092334] hub 1-0:1.0: USB hub found
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092339] hub 1-0:1.0: 8 ports detected
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092428] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092440] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092452] ohci_hcd 0000:00:13.0: OHCI Host Controller
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092487] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Dec  2 19:11:06 sebastian-laptop kernel: [    1.092504] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
Dec  2 19:11:06 sebastian-laptop kernel: [    1.156419] hub 2-0:1.0: USB hub found
Dec  2 19:11:06 sebastian-laptop kernel: [    1.156432] hub 2-0:1.0: 4 ports detected
Dec  2 19:11:06 sebastian-laptop kernel: [    1.156517] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec  2 19:11:06 sebastian-laptop kernel: [    1.156543] ohci_hcd 0000:00:13.1: OHCI Host Controller
Dec  2 19:11:06 sebastian-laptop kernel: [    1.156586] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Dec  2 19:11:06 sebastian-laptop kernel: [    1.156611] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
Dec  2 19:11:06 sebastian-laptop kernel: [    1.235878] hub 3-0:1.0: USB hub found
Dec  2 19:11:06 sebastian-laptop kernel: [    1.235888] hub 3-0:1.0: 4 ports detected
Dec  2 19:11:06 sebastian-laptop kernel: [    1.235970] uhci_hcd: USB Universal Host Controller Interface driver
Dec  2 19:11:06 sebastian-laptop kernel: [    1.240141] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Dec  2 19:11:06 sebastian-laptop kernel: [    1.242607] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243570] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243576] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243606] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243636] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243660] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243786] mice: PS/2 mouse device common for all mice
Dec  2 19:11:06 sebastian-laptop kernel: [    1.243966] rtc_cmos 00:03: RTC can wake from S4
Dec  2 19:11:06 sebastian-laptop kernel: [    1.244030] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec  2 19:11:06 sebastian-laptop kernel: [    1.244059] rtc0: alarms up to one month, 114 bytes nvram
Dec  2 19:11:06 sebastian-laptop kernel: [    1.244173] device-mapper: uevent: version 1.0.3
Dec  2 19:11:06 sebastian-laptop kernel: [    1.252171] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
Dec  2 19:11:06 sebastian-laptop kernel: [    1.252247] device-mapper: multipath: version 1.1.1 loaded
Dec  2 19:11:06 sebastian-laptop kernel: [    1.252250] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254029] EISA: Probing bus 0 at eisa.0
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254034] EISA: Cannot allocate resource for mainboard
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254037] Cannot allocate resource for EISA slot 1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254040] Cannot allocate resource for EISA slot 2
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254042] Cannot allocate resource for EISA slot 3
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254044] Cannot allocate resource for EISA slot 4
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254047] Cannot allocate resource for EISA slot 5
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254049] Cannot allocate resource for EISA slot 6
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254052] Cannot allocate resource for EISA slot 7
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254054] Cannot allocate resource for EISA slot 8
Dec  2 19:11:06 sebastian-laptop kernel: [    1.254056] EISA: Detected 0 cards.
Dec  2 19:11:06 sebastian-laptop kernel: [    1.258560] cpuidle: using governor ladder
Dec  2 19:11:06 sebastian-laptop kernel: [    1.258624] cpuidle: using governor menu
Dec  2 19:11:06 sebastian-laptop kernel: [    1.258916] TCP cubic registered
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259055] NET: Registered protocol family 10
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259432] lo: Disabled Privacy Extensions
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259641] NET: Registered protocol family 17
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259677] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-37 (1 cpu cores) (version 2.20.00)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259725] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x4
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259728] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259731] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x8
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259733] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x16
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259774] Using IPI No-Shortcut mode
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259874] PM: Resume from disk failed.
Dec  2 19:11:06 sebastian-laptop kernel: [    1.259885] registered taskstats version 1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.260173]   Magic number: 6:872:151
Dec  2 19:11:06 sebastian-laptop kernel: [    1.260197] bdi 1:3: hash matches
Dec  2 19:11:06 sebastian-laptop kernel: [    1.260234] pci 0000:00:14.4: hash matches
Dec  2 19:11:06 sebastian-laptop kernel: [    1.260294] rtc_cmos 00:03: setting system clock to 2010-12-03 00:10:42 UTC (1291335042)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.260297] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  2 19:11:06 sebastian-laptop kernel: [    1.260299] EDD information not available.
Dec  2 19:11:06 sebastian-laptop kernel: [    1.276111] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Dec  2 19:11:06 sebastian-laptop kernel: [    1.690386] Freeing initrd memory: 10504k freed
Dec  2 19:11:06 sebastian-laptop kernel: [    1.745865] isapnp: No Plug & Play device found
Dec  2 19:11:06 sebastian-laptop kernel: [    1.745882] Freeing unused kernel memory: 684k freed
Dec  2 19:11:06 sebastian-laptop kernel: [    1.746797] Write protecting the kernel text: 4932k
Dec  2 19:11:06 sebastian-laptop kernel: [    1.746828] Write protecting the kernel read-only data: 1976k
Dec  2 19:11:06 sebastian-laptop kernel: [    1.762205] udev[65]: starting version 163
Dec  2 19:11:06 sebastian-laptop kernel: [    1.958720] tg3.c:v3.110 (April 9, 2010)
Dec  2 19:11:06 sebastian-laptop kernel: [    1.958742]   alloc irq_desc for 18 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.958745]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [    1.958752] tg3 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  2 19:11:06 sebastian-laptop kernel: [    1.958761] tg3 0000:05:00.0: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [    1.977899] scsi0 : pata_atiixp
Dec  2 19:11:06 sebastian-laptop kernel: [    2.004820] scsi1 : pata_atiixp
Dec  2 19:11:06 sebastian-laptop kernel: [    2.005622] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
Dec  2 19:11:06 sebastian-laptop kernel: [    2.005626] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
Dec  2 19:11:06 sebastian-laptop kernel: [    2.038923] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
Dec  2 19:11:06 sebastian-laptop kernel: [    2.040486] tg3 0000:05:00.0: eth0: Tigon3 [partno(BCM95789) rev 4101] (PCI Express) MAC address 00:16:36:24:fb:7b
Dec  2 19:11:06 sebastian-laptop kernel: [    2.040491] tg3 0000:05:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Dec  2 19:11:06 sebastian-laptop kernel: [    2.040494] tg3 0000:05:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Dec  2 19:11:06 sebastian-laptop kernel: [    2.040497] tg3 0000:05:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Dec  2 19:11:06 sebastian-laptop kernel: [    2.056079] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
Dec  2 19:11:06 sebastian-laptop kernel: [    2.056089] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
Dec  2 19:11:06 sebastian-laptop kernel: [    2.056099] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
Dec  2 19:11:06 sebastian-laptop kernel: [    2.056108] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
Dec  2 19:11:06 sebastian-laptop kernel: [    2.096109] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
Dec  2 19:11:06 sebastian-laptop kernel: [    2.096136] firewire_ohci 0000:06:09.2: PCI INT C -> GSI 21 (level, low) -> IRQ 9
Dec  2 19:11:06 sebastian-laptop kernel: [    2.152087] firewire_ohci: Added fw-ohci device 0000:06:09.2, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Dec  2 19:11:06 sebastian-laptop kernel: [    2.169239] ata2.00: ATAPI: MATSHITADVD-RAM UJ-845S, D200, max UDMA/33
Dec  2 19:11:06 sebastian-laptop kernel: [    2.184665] ata2.00: configured for UDMA/33
Dec  2 19:11:06 sebastian-laptop kernel: [    2.218540] ata1.00: ATA-8: WDC WD3200BEVE-00A0HT0, 11.01A11, max UDMA/100
Dec  2 19:11:06 sebastian-laptop kernel: [    2.218543] ata1.00: 625142448 sectors, multi 16: LBA48 
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233399] ata1.00: configured for UDMA/100
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233504] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVE-0 11.0 PQ: 0 ANSI: 5
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233650] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233905] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233951] sd 0:0:0:0: [sda] Write Protect is off
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233954] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec  2 19:11:06 sebastian-laptop kernel: [    2.233975] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  2 19:11:06 sebastian-laptop kernel: [    2.234103]  sda:
Dec  2 19:11:06 sebastian-laptop kernel: [    2.235727] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-845S  D200 PQ: 0 ANSI: 5
Dec  2 19:11:06 sebastian-laptop kernel: [    2.236503]  sda1 < sda5sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
Dec  2 19:11:06 sebastian-laptop kernel: [    2.240358] Uniform CD-ROM driver Revision: 3.20
Dec  2 19:11:06 sebastian-laptop kernel: [    2.240628] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec  2 19:11:06 sebastian-laptop kernel: [    2.240725] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec  2 19:11:06 sebastian-laptop kernel: [    2.249962]  sda6 sda7 >
Dec  2 19:11:06 sebastian-laptop kernel: [    2.270999] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  2 19:11:06 sebastian-laptop kernel: [    2.652147] firewire_core: created device fw0: GUID 00c09f000089b4fe, S400
Dec  2 19:11:06 sebastian-laptop kernel: [    2.661094] EXT3-fs: barriers not enabled
Dec  2 19:11:06 sebastian-laptop kernel: [    2.670455] kjournald starting.  Commit interval 5 seconds
Dec  2 19:11:06 sebastian-laptop kernel: [    2.670538] EXT3-fs (sda5): mounted filesystem with ordered data mode
Dec  2 19:11:06 sebastian-laptop kernel: [   23.245207] udev[332]: starting version 163
Dec  2 19:11:06 sebastian-laptop kernel: [   23.334566] lp: driver loaded but no devices found
Dec  2 19:11:06 sebastian-laptop kernel: [   23.435495] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
Dec  2 19:11:06 sebastian-laptop kernel: [   23.722150] Linux agpgart interface v0.103
Dec  2 19:11:06 sebastian-laptop kernel: [   23.759720] yenta_cardbus 0000:06:09.0: CardBus bridge found [1025:007e]
Dec  2 19:11:06 sebastian-laptop kernel: [   23.759750] yenta_cardbus 0000:06:09.0: Using CSCINT to route CSC interrupts to PCI
Dec  2 19:11:06 sebastian-laptop kernel: [   23.759753] yenta_cardbus 0000:06:09.0: Routing CardBus interrupts to PCI
Dec  2 19:11:06 sebastian-laptop kernel: [   23.759760] yenta_cardbus 0000:06:09.0: TI: mfunc 0x01721b22, devctl 0x64
Dec  2 19:11:06 sebastian-laptop kernel: [   23.795956] EXT3-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
Dec  2 19:11:06 sebastian-laptop kernel: [   23.826517] parport_pc 00:0b: reported by Plug and Play ACPI
Dec  2 19:11:06 sebastian-laptop kernel: [   23.826690] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Dec  2 19:11:06 sebastian-laptop kernel: [   23.873735] EXT3-fs (sda5): using internal journal
Dec  2 19:11:06 sebastian-laptop kernel: [   23.901531] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:09/LNXVIDEO:00/input/input5
Dec  2 19:11:06 sebastian-laptop kernel: [   23.901659] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec  2 19:11:06 sebastian-laptop kernel: [   23.904892] lp0: using parport0 (interrupt-driven).
Dec  2 19:11:06 sebastian-laptop kernel: [   23.935469] ppdev: user-space parallel port driver
Dec  2 19:11:06 sebastian-laptop kernel: [   23.988577] irda_init()
Dec  2 19:11:06 sebastian-laptop kernel: [   23.988597] NET: Registered protocol family 23
Dec  2 19:11:06 sebastian-laptop kernel: [   23.997323] yenta_cardbus 0000:06:09.0: ISA IRQ mask 0x0c78, PCI irq 23
Dec  2 19:11:06 sebastian-laptop kernel: [   23.997329] yenta_cardbus 0000:06:09.0: Socket status: 30000006
Dec  2 19:11:06 sebastian-laptop kernel: [   23.997334] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Dec  2 19:11:06 sebastian-laptop kernel: [   23.997345] yenta_cardbus 0000:06:09.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
Dec  2 19:11:06 sebastian-laptop kernel: [   23.997349] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff
Dec  2 19:11:06 sebastian-laptop kernel: [   24.016837] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.016903] nsc-ircc, chip->init
Dec  2 19:11:06 sebastian-laptop kernel: [   24.016918] nsc-ircc, Found chip at base=0x02e
Dec  2 19:11:06 sebastian-laptop kernel: [   24.016961] nsc-ircc, driver loaded (Dag Brattli)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017160] nsc_ircc_open(), can't get iobase of 0x2f8
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017209] nsc-ircc, Found chip at base=0x02e
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017251] nsc-ircc, driver loaded (Dag Brattli)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017255] nsc_ircc_open(), can't get iobase of 0x2f8
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017275] nsc-ircc, chip->init
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017289] nsc-ircc, Found chip at base=0x02e
Dec  2 19:11:06 sebastian-laptop kernel: [   24.017331] nsc-ircc, driver loaded (Dag Brattli)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.018018] nsc-ircc 00:09: disabled
Dec  2 19:11:06 sebastian-laptop kernel: [   24.021857] cfg80211: Calling CRDA to update world regulatory domain
Dec  2 19:11:06 sebastian-laptop kernel: [   24.032559] 
Dec  2 19:11:06 sebastian-laptop kernel: [   24.032566] yenta_cardbus 0000:06:09.0: pcmcia: parent PCI bridge window: [mem 0xc0300000-0xc03fffff]
Dec  2 19:11:06 sebastian-laptop kernel: [   24.032572] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0300000-0xc03fffff: excluding 0xc0300000-0xc030ffff
Dec  2 19:11:06 sebastian-laptop kernel: [   24.032585] yenta_cardbus 0000:06:09.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref]
Dec  2 19:11:06 sebastian-laptop kernel: [   24.032588] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff: excluding 0x60000000-0x63ffffff
Dec  2 19:11:06 sebastian-laptop kernel: [   24.075199] tifm_7xx1 0000:06:09.3: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105941] cfg80211: World regulatory domain updated:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105945]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105948]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105952]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105955]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105958]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.105961]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.109312] [drm] Initialized drm 1.1.0 20060810
Dec  2 19:11:06 sebastian-laptop kernel: [   24.114692] type=1400 audit(1291335065.351:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=634 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   24.115007] type=1400 audit(1291335065.351:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   24.115192] type=1400 audit(1291335065.351:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   24.174540] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x280-0x297 0x2f8-0x2ff 0x370-0x37f
Dec  2 19:11:06 sebastian-laptop kernel: [   24.176862] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x408-0x40f 0x4d0-0x4d7
Dec  2 19:11:06 sebastian-laptop kernel: [   24.177836] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
Dec  2 19:11:06 sebastian-laptop kernel: [   24.178665] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
Dec  2 19:11:06 sebastian-laptop kernel: [   24.179439] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
Dec  2 19:11:06 sebastian-laptop kernel: [   24.179490] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.179542] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
Dec  2 19:11:06 sebastian-laptop kernel: [   24.179603] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.254275] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.377211] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  2 19:11:06 sebastian-laptop kernel: [   24.384127] [drm] radeon defaulting to kernel modesetting.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.384131] [drm] radeon kernel modesetting enabled.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.384212] radeon 0000:01:00.0: power state changed by ACPI to D0
Dec  2 19:11:06 sebastian-laptop kernel: [   24.384220] radeon 0000:01:00.0: power state changed by ACPI to D0
Dec  2 19:11:06 sebastian-laptop kernel: [   24.384229] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  2 19:11:06 sebastian-laptop kernel: [   24.384235] radeon 0000:01:00.0: setting latency timer to 64
Dec  2 19:11:06 sebastian-laptop kernel: [   24.392789] [drm] initializing kernel modesetting (RV410 0x1002:0x5653).
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396258] [drm] register mmio base: 0xC0100000
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396260] [drm] register mmio size: 65536
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396425] ATOM BIOS: Quanta/Acer
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396464] [drm] Generation 2 PCI interface, using max accessible memory
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396470] radeon 0000:01:00.0: VRAM: 128M 0xC8000000 - 0xCFFFFFFF (128M used)
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396474] radeon 0000:01:00.0: GTT: 512M 0xA8000000 - 0xC7FFFFFF
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396525]   alloc irq_desc for 42 on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396528]   alloc kstat_irqs on node -1
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396539] radeon 0000:01:00.0: irq 42 for MSI/MSI-X
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396544] radeon 0000:01:00.0: radeon: using MSI.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396573] [drm] radeon: irq initialized.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396792] [drm] Detected VRAM RAM=128M, BAR=128M
Dec  2 19:11:06 sebastian-laptop kernel: [   24.396798] [drm] RAM width 128bits DDR
Dec  2 19:11:06 sebastian-laptop kernel: [   24.402114] [TTM] Zone  kernel: Available graphics memory: 439922 kiB.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.402117] [TTM] Zone highmem: Available graphics memory: 771158 kiB.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.402119] [TTM] Initializing pool allocator.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.402140] [drm] radeon: 128M of VRAM memory ready
Dec  2 19:11:06 sebastian-laptop kernel: [   24.402143] [drm] radeon: 512M of GTT memory ready.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.402166] [drm] GART: num cpu pages 131072, num gpu pages 131072
Dec  2 19:11:06 sebastian-laptop kernel: [   24.404561] [drm] PCIE GART of 512M enabled (table at 0xC8040000).
Dec  2 19:11:06 sebastian-laptop kernel: [   24.404572] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.405243] [drm] Loading R400 Microcode
Dec  2 19:11:06 sebastian-laptop kernel: [   24.406901] [drm] radeon: ring at 0x00000000A8000000
Dec  2 19:11:06 sebastian-laptop kernel: [   24.406925] [drm] ring test succeeded in 1 usecs
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407056] [drm] radeon: ib pool ready.
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407128] [drm] ib test succeeded in 0 usecs
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407166] [drm] Default TV standard: NTSC
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407286] [drm] Default TV standard: NTSC
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407357] [drm] Radeon Display Connectors
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407359] [drm] Connector 0:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407361] [drm]   VGA
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407364] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407366] [drm]   Encoders:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407368] [drm]     CRT1: INTERNAL_DAC1
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407369] [drm] Connector 1:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407371] [drm]   LVDS
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407373] [drm]   DDC: 0x1a8 0x1a8 0x1ac 0x1ac 0x1b0 0x1b0 0x1b4 0x1b4
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407375] [drm]   Encoders:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407377] [drm]     LCD1: INTERNAL_LVDS
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407379] [drm] Connector 2:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407380] [drm]   S-video
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407382] [drm]   Encoders:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407383] [drm]     TV1: INTERNAL_DAC2
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407385] [drm] Connector 3:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407386] [drm]   DVI-I
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407388] [drm]   HPD1
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407390] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407392] [drm]   Encoders:
Dec  2 19:11:06 sebastian-laptop kernel: [   24.407394] [drm]     DFP1: INTERNAL_TMDS1
Dec  2 19:11:06 sebastian-laptop kernel: [   24.430358] phy0: Selected rate control algorithm 'minstrel'
Dec  2 19:11:06 sebastian-laptop kernel: [   24.431023] Registered led device: b43-phy0::tx
Dec  2 19:11:06 sebastian-laptop kernel: [   24.431045] Registered led device: b43-phy0::rx
Dec  2 19:11:06 sebastian-laptop kernel: [   24.431067] Registered led device: b43-phy0::radio
Dec  2 19:11:06 sebastian-laptop kernel: [   24.431138] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
Dec  2 19:11:06 sebastian-laptop kernel: [   24.531117] [drm] radeon: power management initialized
Dec  2 19:11:06 sebastian-laptop kernel: [   24.905440] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> NetworkManager (version 0.8.1) is starting...
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Dec  2 19:11:06 sebastian-laptop kernel: [   24.996959] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000/0x0
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Successfully dropped root privileges.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> trying to start the modem manager...
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: avahi-daemon 0.6.27 starting up.
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Successfully called chroot().
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Successfully dropped remaining capabilities.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: init!
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: update_system_hostname
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPluginIfupdown: management mode: unmanaged
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/net/eth0, iface: eth0)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: end _init.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    Ifupdown: get unmanaged devices count: 0
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: (149359952) ... get_connections.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    SCPlugin-Ifupdown: (149359952) ... get_connections (managed=false): return empty list.
Dec  2 19:11:06 sebastian-laptop modem-manager: ModemManager (version 0.4) starting...
Dec  2 19:11:06 sebastian-laptop kernel: [   25.059203] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: No service file found in /etc/avahi/services.
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Nokia
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin AnyData
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Ericsson MBM
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin MotoC
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Option High-Speed
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Gobi
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin SimTech
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]:    Ifupdown: get unmanaged devices count: 0
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:14.4/0000:06:02.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> Networking is enabled by state file
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): carrier is OFF
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): now managed
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): bringing up device.
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Novatel
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Option
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Longcheer
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin ZTE
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Generic
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Sierra
Dec  2 19:11:06 sebastian-laptop modem-manager: Loaded plugin Huawei
Dec  2 19:11:06 sebastian-laptop modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Dec  2 19:11:06 sebastian-laptop modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Dec  2 19:11:06 sebastian-laptop modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Dec  2 19:11:06 sebastian-laptop modem-manager: (tty/ttyS0): could not get port's parent device
Dec  2 19:11:06 sebastian-laptop kernel: [   25.253804] type=1400 audit(1291335066.491:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=847 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   25.266537] type=1400 audit(1291335066.503:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=851 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   25.267101] type=1400 audit(1291335066.503:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=851 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   25.267286] type=1400 audit(1291335066.503:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=851 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   25.283941] type=1400 audit(1291335066.519:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=857 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   25.290496] type=1400 audit(1291335066.527:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=857 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop kernel: [   25.295546] type=1400 audit(1291335066.531:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=857 comm="apparmor_parser"
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Network interface enumeration completed.
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Registering HINFO record with values 'I686'/'LINUX'.
Dec  2 19:11:06 sebastian-laptop avahi-daemon[815]: Server startup complete. Host name is sebastian-laptop.local. Local service cookie is 617767983.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): preparing device.
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (eth0): deactivating device (reason: 2).
Dec  2 19:11:06 sebastian-laptop kernel: [   25.341287] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/net/eth0
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (wlan0): now managed
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Dec  2 19:11:06 sebastian-laptop NetworkManager[810]: <info> (wlan0): bringing up device.
Dec  2 19:11:06 sebastian-laptop kernel: [   25.526665] [drm] fb mappable at 0xC80C0000
Dec  2 19:11:06 sebastian-laptop kernel: [   25.526669] [drm] vram apper at 0xC8000000
Dec  2 19:11:06 sebastian-laptop kernel: [   25.526672] [drm] size 4096000
Dec  2 19:11:06 sebastian-laptop kernel: [   25.526673] [drm] fb depth is 24
Dec  2 19:11:06 sebastian-laptop kernel: [   25.526675] [drm]    pitch is 5120
Dec  2 19:11:07 sebastian-laptop cron[932]: (CRON) INFO (pidfile fd = 3)
Dec  2 19:11:07 sebastian-laptop init: apport pre-start process (924) terminated with status 1
Dec  2 19:11:07 sebastian-laptop acpid: starting up with proc fs
Dec  2 19:11:07 sebastian-laptop acpid: 36 rules loaded
Dec  2 19:11:07 sebastian-laptop init: apport post-stop process (946) terminated with status 1
Dec  2 19:11:07 sebastian-laptop acpid: waiting for events: event logging is off
Dec  2 19:11:07 sebastian-laptop anacron[974]: Anacron 2.3 started on 2010-12-02
Dec  2 19:11:07 sebastian-laptop cron[980]: (CRON) STARTUP (fork ok)
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> (wlan0): preparing device.
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> (wlan0): deactivating device (reason: 2).
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Dec  2 19:11:07 sebastian-laptop cron[980]: (CRON) INFO (Running @reboot jobs)
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> modem-manager is now available
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> Trying to start the supplicant...
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant manager state:  down -> idle
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Dec  2 19:11:07 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant interface state:  starting -> ready
Dec  2 19:11:07 sebastian-laptop anacron[974]: Normal exit (0 jobs run)
Dec  2 19:11:07 sebastian-laptop kernel: [   25.840423] apm: BIOS not found.
Dec  2 19:11:07 sebastian-laptop kernel: [   25.866012] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec  2 19:11:07 sebastian-laptop kernel: [   25.912733] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  2 19:11:07 sebastian-laptop kernel: [   26.174100] Console: switching to colour frame buffer device 160x50
Dec  2 19:11:07 sebastian-laptop kernel: [   26.179544] fb0: radeondrmfb frame buffer device
Dec  2 19:11:07 sebastian-laptop kernel: [   26.179546] drm: registered panic notifier
Dec  2 19:11:07 sebastian-laptop kernel: [   26.184582] Slow work thread pool: Starting up
Dec  2 19:11:07 sebastian-laptop kernel: [   26.184649] Slow work thread pool: Ready
Dec  2 19:11:07 sebastian-laptop kernel: [   26.184660] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
Dec  2 19:11:07 sebastian-laptop gdm-binary[1016]: WARNING: Unable to find users: no seat-id found
Dec  2 19:11:07 sebastian-laptop acpid: client connected from 1104[0:0]
Dec  2 19:11:07 sebastian-laptop acpid: 1 client rule loaded
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> (eth0): carrier now ON (device state 2)
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) starting connection 'Auto eth0'
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Dec  2 19:11:08 sebastian-laptop kernel: [   26.800127] tg3 0000:05:00.0: eth0: Link is up at 100 Mbps, full duplex
Dec  2 19:11:08 sebastian-laptop kernel: [   26.800132] tg3 0000:05:00.0: eth0: Flow control is on for TX and on for RX
Dec  2 19:11:08 sebastian-laptop kernel: [   26.800383] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> dhclient started with pid 1121
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  2 19:11:08 sebastian-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec  2 19:11:08 sebastian-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec  2 19:11:08 sebastian-laptop dhclient: All rights reserved.
Dec  2 19:11:08 sebastian-laptop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec  2 19:11:08 sebastian-laptop dhclient: 
Dec  2 19:11:08 sebastian-laptop NetworkManager[810]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  2 19:11:08 sebastian-laptop dhclient: Listening on LPF/eth0/00:16:36:24:fb:7b
Dec  2 19:11:08 sebastian-laptop dhclient: Sending on   LPF/eth0/00:16:36:24:fb:7b
Dec  2 19:11:08 sebastian-laptop dhclient: Sending on   Socket/fallback
Dec  2 19:11:08 sebastian-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Successfully called chroot.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Successfully dropped privileges.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Successfully limited resources.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Running.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Canary thread running.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Watchdog thread running.
Dec  2 19:11:09 sebastian-laptop polkitd[1310]: started daemon version 0.96 using authority implementation `local' version `0.96'
Dec  2 19:11:09 sebastian-laptop avahi-daemon[815]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::216:36ff:fe24:fb7b.
Dec  2 19:11:09 sebastian-laptop avahi-daemon[815]: New relevant interface eth0.IPv6 for mDNS.
Dec  2 19:11:09 sebastian-laptop avahi-daemon[815]: Registering new address record for fe80::216:36ff:fe24:fb7b on eth0.*.
Dec  2 19:11:09 sebastian-laptop init: plymouth-stop pre-start process (1341) terminated with status 1
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Successfully made thread 1297 of process 1297 (n/a) owned by '105' high priority at nice level -11.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Supervising 1 threads of 1 processes of 1 users.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Successfully made thread 1343 of process 1297 (n/a) owned by '105' RT at priority 5.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Supervising 2 threads of 1 processes of 1 users.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Successfully made thread 1344 of process 1297 (n/a) owned by '105' RT at priority 5.
Dec  2 19:11:09 sebastian-laptop rtkit-daemon[1302]: Supervising 3 threads of 1 processes of 1 users.
Dec  2 19:11:10 sebastian-laptop gdm-simple-greeter[1271]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Dec  2 19:11:10 sebastian-laptop gdm-simple-greeter[1271]: WARNING: Unable to lookup user name sebastia: Success
Dec  2 19:11:11 sebastian-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec  2 19:11:11 sebastian-laptop dhclient: DHCPOFFER of 192.168.1.57 from 192.168.1.1
Dec  2 19:11:11 sebastian-laptop dhclient: DHCPREQUEST of 192.168.1.57 on eth0 to 255.255.255.255 port 67
Dec  2 19:11:11 sebastian-laptop dhclient: DHCPACK of 192.168.1.57 from 192.168.1.1
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info>   address 192.168.1.57
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info>   prefix 24 (255.255.255.0)
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info>   gateway 192.168.1.1
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info>   nameserver '192.168.1.1'
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  2 19:11:11 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec  2 19:11:11 sebastian-laptop avahi-daemon[815]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.57.
Dec  2 19:11:11 sebastian-laptop avahi-daemon[815]: New relevant interface eth0.IPv4 for mDNS.
Dec  2 19:11:11 sebastian-laptop avahi-daemon[815]: Registering new address record for 192.168.1.57 on eth0.IPv4.
Dec  2 19:11:11 sebastian-laptop dhclient: bound to 192.168.1.57 -- renewal in 41063 seconds.
Dec  2 19:11:11 sebastian-laptop gdm-session-worker[1281]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Dec  2 19:11:12 sebastian-laptop NetworkManager[810]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Dec  2 19:11:12 sebastian-laptop NetworkManager[810]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Dec  2 19:11:12 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) successful, device activated.
Dec  2 19:11:12 sebastian-laptop NetworkManager[810]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec  2 19:11:13 sebastian-laptop ntpdate[1476]: step time server 91.189.94.4 offset 0.596094 sec
Dec  2 19:11:14 sebastian-laptop NetworkManager[810]: <error> [1291335074.277569] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec  2 19:11:14 sebastian-laptop NetworkManager[810]: <error> [1291335074.326809] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec  2 19:11:15 sebastian-laptop rtkit-daemon[1302]: Successfully made thread 1594 of process 1594 (n/a) owned by '1000' high priority at nice level -11.
Dec  2 19:11:15 sebastian-laptop rtkit-daemon[1302]: Supervising 4 threads of 2 processes of 2 users.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) starting connection 'Auto flamingonet'
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0/wireless): access point 'Auto flamingonet' has security, but secrets are required.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0/wireless): connection 'Auto flamingonet' has security, and secrets exist.  No new secrets needed.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Config: added 'ssid' value 'flamingonet'
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Config: added 'scan_ssid' value '1'
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Config: added 'psk' value '<omitted>'
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> Config: set interface ap_scan to 1
Dec  2 19:11:18 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Dec  2 19:11:18 sebastian-laptop kernel: [   37.072026] eth0: no IPv6 routers present
Dec  2 19:11:20 sebastian-laptop wpa_supplicant[987]: Trying to associate with 00:26:f2:9c:d2:9c (SSID='flamingonet' freq=2412 MHz)
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  2 19:11:20 sebastian-laptop kernel: [   38.282251] wlan0: authenticate with 00:26:f2:9c:d2:9c (try 1)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.283653] wlan0: authenticated
Dec  2 19:11:20 sebastian-laptop kernel: [   38.284897] wlan0: associate with 00:26:f2:9c:d2:9c (try 1)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.287360] wlan0: RX AssocResp from 00:26:f2:9c:d2:9c (capab=0x431 status=0 aid=2)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.287363] wlan0: associated
Dec  2 19:11:20 sebastian-laptop wpa_supplicant[987]: Associated with 00:26:f2:9c:d2:9c
Dec  2 19:11:20 sebastian-laptop kernel: [   38.288472] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec  2 19:11:20 sebastian-laptop kernel: [   38.288615] cfg80211: Calling CRDA for country: US
Dec  2 19:11:20 sebastian-laptop wpa_supplicant[987]: WPA: Key negotiation completed with 00:26:f2:9c:d2:9c [PTK=TKIP GTK=TKIP]
Dec  2 19:11:20 sebastian-laptop wpa_supplicant[987]: CTRL-EVENT-CONNECTED - Connection to 00:26:f2:9c:d2:9c completed (auth) [id=0 id_str=]
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant connection state:  associating -> associated
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'flamingonet'.
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323910] cfg80211: Received country IE:
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323914] cfg80211: Regulatory domain: US
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323916]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323920]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323922] cfg80211: CRDA thinks this should applied:
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323924] cfg80211: Regulatory domain: US
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323926]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323929]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323932]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323935]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323938]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323941]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323944]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323946] cfg80211: We intersect both of these and get:
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323947] cfg80211: Regulatory domain: 98
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323949]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323952]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323958] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323961] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323963] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323967] cfg80211: Current regulatory domain updated by AP to: US
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323969]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  2 19:11:20 sebastian-laptop kernel: [   38.323972]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> dhclient started with pid 1727
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec  2 19:11:20 sebastian-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec  2 19:11:20 sebastian-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec  2 19:11:20 sebastian-laptop dhclient: All rights reserved.
Dec  2 19:11:20 sebastian-laptop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec  2 19:11:20 sebastian-laptop dhclient: 
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec  2 19:11:20 sebastian-laptop dhclient: Listening on LPF/wlan0/00:14:a4:3c:d6:a6
Dec  2 19:11:20 sebastian-laptop dhclient: Sending on   LPF/wlan0/00:14:a4:3c:d6:a6
Dec  2 19:11:20 sebastian-laptop dhclient: Sending on   Socket/fallback
Dec  2 19:11:20 sebastian-laptop dhclient: DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67
Dec  2 19:11:20 sebastian-laptop dhclient: DHCPACK of 192.168.1.66 from 192.168.1.1
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info>   address 192.168.1.66
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info>   prefix 24 (255.255.255.0)
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info>   gateway 192.168.1.1
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info>   nameserver '192.168.1.1'
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  2 19:11:20 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec  2 19:11:20 sebastian-laptop avahi-daemon[815]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.66.
Dec  2 19:11:20 sebastian-laptop avahi-daemon[815]: New relevant interface wlan0.IPv4 for mDNS.
Dec  2 19:11:20 sebastian-laptop avahi-daemon[815]: Registering new address record for 192.168.1.66 on wlan0.IPv4.
Dec  2 19:11:20 sebastian-laptop dhclient: bound to 192.168.1.66 -- renewal in 41961 seconds.
Dec  2 19:11:21 sebastian-laptop NetworkManager[810]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Dec  2 19:11:21 sebastian-laptop NetworkManager[810]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Dec  2 19:11:21 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) successful, device activated.
Dec  2 19:11:21 sebastian-laptop NetworkManager[810]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.

---

### Post by SebSmith on 2010-12-02
im no longer getting dependency errors, but this black screen after selecting kernel is annoying. the blinky is the for 15-26 seconds.

---

