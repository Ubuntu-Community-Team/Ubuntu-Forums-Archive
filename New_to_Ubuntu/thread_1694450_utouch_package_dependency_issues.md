---
title: "utouch package dependency issues"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by openick on 2011-02-24
Would someone please take a look at this and tell me what I should do?

(Version installed 10.04  (10.10 netbook version had some problems)

HW:  Touch tablet

[COLOR="MediumTurquoise"]dpkg -i libmtdev1_1.1.0-1_i386.deb 
Selecting previously deselected package libmtdev1.
(Reading database ... 147373 files and directories currently installed.)
Unpacking libmtdev1 (from libmtdev1_1.1.0-1_i386.deb) ...
Setting up libmtdev1 (1.1.0-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/COLOR]

root@tab-touch:/home/tab/Downloads# dpkg -i libmtdev-dev_1.0.10-0ubuntu1_i386.deb 
(Reading database ... 147381 files and directories currently installed.)
Preparing to replace libmtdev-dev 1.0.10-0ubuntu1 (using libmtdev-dev_1.0.10-0ubuntu1_i386.deb) ...
Unpacking replacement libmtdev-dev ...
dpkg: dependency problems prevent configuration of libmtdev-dev:
 libmtdev-dev depends on libmtdev1 (= 1.0.10-0ubuntu1); however:
  [COLOR="red"]Version of libmtdev1 on system is 1.1.0-1[/COLOR].
dpkg: error processing libmtdev-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmtdev-dev


root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis-dev_1.0.11-0ubuntu1_i386.deb 
Selecting previously deselected package libutouch-geis-dev.
(Reading database ... 147381 files and directories currently installed.)
Unpacking libutouch-geis-dev (from libutouch-geis-dev_1.0.11-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libutouch-geis-dev:
 libutouch-geis-dev depends on libutouch-geis1 (= 1.0.11-0ubuntu1); however:
  Package libutouch-geis1 is not installed.
dpkg: error processing libutouch-geis-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libutouch-geis-dev
root@tab-touch:/home/tab/Downloads# DPKG -i utouch_1.1_all.deb 
DPKG: command not found
root@tab-touch:/home/tab/Downloads# dpkg -i utouch_1.1_all.deb 
(Reading database ... 147389 files and directories currently installed.)
Preparing to replace utouch 1.1 (using utouch_1.1_all.deb) ...
Unpacking replacement utouch ...
dpkg: dependency problems prevent configuration of utouch:

utouch depends on libmtdev-dev; however:
  Package [COLOR="Red"]libmtdev-dev is not configured yet[/COLOR].
 utouch depends on mtdev-tools; however:
  Package mtdev-tools is not configured yet.
 utouch depends on libutouch-grail-dev; however:
  Package libutouch-grail-dev is not installed.
 utouch depends on utouch-grail-tools; however:
  Package utouch-grail-tools is not installed.
 utouch depends on utouch-gesturetest; however:
  Package utouch-gesturetest is not installed.
 utouch depends on libutouch-geis-dev; however:
  Package libutouch-geis-dev is not configured yet.
 utouch depends on libutouch-geis-doc; however:
  Package libutouch-geis-doc is not installed.
 utouch depends on utouch-geis-tools; however:
  Package utouch-geis-tools is not installed.
dpkg: error processing utouch (--install):
 dependency problems - leaving unconfigured

[COLOR="Blue"]Files in my Downloads directory;

ginn_0.2.4-0ubuntu1.debian.tar.gz
ginn_0.2.4-0ubuntu1.dsc
ginn_0.2.4.orig.tar.gz
libmtdev1_1.1.0-1_i386.deb
libmtdev-dev_1.0.10-0ubuntu1_i386.deb
libutouch-geis-dev_1.0.11-0ubuntu1_i386.deb
libutouch-geis-doc_1.0.11-0ubuntu1_all.deb
libutouch-grail-dev_1.0.16-0ubuntu1_i386.deb
mtdev-tools_1.0.10-0ubuntu1_i386.deb
Packages
Packages.bz2
utouch_1.1_all.deb
utouch-geis-tools_1.0.11-0ubuntu1_i386.deb
utouch-gesturetest_1.0.4-0ubuntu1.debian.tar.gz
utouch-gesturetest_1.0.4-0ubuntu1_i386.deb
utouch-gesturetest_1.0.4.orig.tar.gz
utouch-grail-tools_1.0.16-0ubuntu1_i386.deb[/COLOR]

---

### Post by Perfect Storm on 2011-02-24
Are those debs from natty? 

If not try with natty .deb (still in development), if you're lucky you don't run into dependency issue, as they might require newer libs: [http://packages.ubuntu.com/search?keywords=+libmtdev1&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=+libmtdev1&searchon=names&suite=natty&section=all)

---

### Post by openick on 2011-02-24
> **Artificial Intelligence said:**
> Are those debs from natty? 

If not [COLOR="Navy"]**try with natty .deb **[/COLOR](still in development), if you're lucky you don't run into dependency issue, as they might require newer libs: [http://packages.ubuntu.com/search?keywords=+libmtdev1&searchon=names&suite=natty&section=all](http://packages.ubuntu.com/search?keywords=+libmtdev1&searchon=names&suite=natty&section=all)

[SIZE="3"][COLOR="DarkSlateBlue"]**Thank you**[/COLOR][/SIZE]. I removed the files in my Downloads directory ealier downloaded from the other projects, and have downloaded all natty packages 

I am progressing, but possibly am making two mistakes:

1.  The natty packages that I have downloaded include [COLOR="blue"]udeb packages. Possibly for the wrong computer ???[/COLOR], so I skipped them.

2.  The dependency problems are best resolved by adding the sources y on synoptic and let synoptic manage the dependencies, but I d[COLOR="blue"]on't know what to add in the apt line, nor do know how many sources I need to add to get all these files right[/COLOR] to synoptic ( or in the command line to use the apt-get command )

[COLOR="Blue"]Some progress, but still going round and round with an increasingly growing list of dependencies.[/COLOR]


root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis1_2.0.1-0ubuntu1_i386.deb
(Reading database ... 147378 files and directories currently installed.)
Preparing to replace libutouch-geis1 2.0.1-0ubuntu1 (using libutouch-geis1_2.0.1-0ubuntu1_i386.deb) ...
Unpacking replacement libutouch-geis1 ...
dpkg: dependency problems prevent configuration of libutouch-geis1:
 [COLOR="red"]libutouch-geis1 depends on libutouch-grail1[/COLOR] (>= 1.0.10); however:
  Package libutouch-grail1 is not installed.
 [COLOR="Red"]libutouch-geis1 depends on libx11-xcb1[/COLOR]; however:
  Package libx11-xcb1 is not installed.
dpkg: error processing libutouch-geis1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libutouch-geis1
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis-dev_1.0.11-0ubuntu1_i386.deb 
dpkg: error processing libutouch-geis-dev_1.0.11-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libutouch-geis-dev_1.0.11-0ubuntu1_i386.deb
root@tab-touch:/home/tab/Downloads# dpkg -i libmtdev1_1.1.0-0ubuntu1_i386.deb 
(Reading database ... 147378 files and directories currently installed.)
Preparing to replace libmtdev1 1.1.0-0ubuntu1 (using libmtdev1_1.1.0-0ubuntu1_i386.deb) ...
Unpacking replacement libmtdev1 ...
Setting up libmtdev1 (1.1.0-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libmtdev1-udeb_1.1.0-0ubuntu1_i386.udeb 
Selecting previously deselected package libmtdev1-udeb.
(Reading database ... 147378 files and directories currently installed.)
Unpacking libmtdev1-udeb (from libmtdev1-udeb_1.1.0-0ubuntu1_i386.udeb) ...
dpkg: error processing libmtdev1-udeb_1.1.0-0ubuntu1_i386.udeb (--install):
 trying to overwrite '/usr/lib/libmtdev.so.1.0.0', which is also in package libmtdev1 0:1.1.0-0ubuntu1
Errors were encountered while processing:
 [COLOR="red"]ibmtdev1-udeb_1.1.0-0ubuntu1_i386.udeb[/COLOR]
root@tab-touch:/home/tab/Downloads# dpkg -i libmtdev-dev_1.1.0-0ubuntu1_i386.deb 
Selecting previously deselected package libmtdev-dev.
(Reading database ... 147378 files and directories currently installed.)
Unpacking libmtdev-dev (from libmtdev-dev_1.1.0-0ubuntu1_i386.deb) ...
Setting up libmtdev-dev (1.1.0-0ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-grail1_1.0.19-0ubuntu2_i386.deb 
Selecting previously deselected package libutouch-grail1.
(Reading database ... 147387 files and directories currently installed.)
Unpacking libutouch-grail1 (from libutouch-grail1_1.0.19-0ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of libutouch-grail1:
 [COLOR="red"]libutouch-grail1 depends on libutouch-evemu1[/COLOR] (>= 1.0.3); however:
  Package libutouch-evemu1 is not installed.
 [COLOR="red"]libutouch-grail1 depends on libutouch-frame1[/COLOR] (>= 1.0.0); however:
  Package libutouch-frame1 is not installed.
dpkg: error processing libutouch-grail1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libutouch-grail1
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-evemu1_1.0.4-0ubuntu1_i386.deb 
Selecting previously deselected package libutouch-evemu1.
(Reading database ... 147393 files and directories currently installed.)
Unpacking libutouch-evemu1 (from libutouch-evemu1_1.0.4-0ubuntu1_i386.deb) ...
[COLOR="DarkGreen"]**Setting up libutouch-evemu1**[/COLOR] (1.0.4-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-evemu-dev_1.0.4-0ubuntu1_i386.deb 
Selecting previously deselected package libutouch-evemu-dev.
(Reading database ... 147399 files and directories currently installed.)
Unpacking libutouch-evemu-dev (from libutouch-evemu-dev_1.0.4-0ubuntu1_i386.deb) ...
Setting up libutouch-evemu-dev (1.0.4-0ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i utouch-evemu-tools_1.0.4-0ubuntu1_i386.deb 
Selecting previously deselected package utouch-evemu-tools.
(Reading database ... 147406 files and directories currently installed.)
Unpacking utouch-evemu-tools (from utouch-evemu-tools_1.0.4-0ubuntu1_i386.deb) ...
Setting up utouch-evemu-tools (1.0.4-0ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-frame1_1.1.1-0ubuntu1_i386.deb 
Selecting previously deselected package libutouch-frame1.
(Reading database ... 147418 files and directories currently installed.)
Unpacking libutouch-frame1 (from libutouch-frame1_1.1.1-0ubuntu1_i386.deb) ...
[COLOR="DarkGreen"]**Setting up libutouch-frame1**[/COLOR] (1.1.1-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-frame-dev_1.1.1-0ubuntu1_i386.deb 
Selecting previously deselected package libutouch-frame-dev.
(Reading database ... 147424 files and directories currently installed.)
Unpacking libutouch-frame-dev (from libutouch-frame-dev_1.1.1-0ubuntu1_i386.deb) ...
Setting up libutouch-frame-dev (1.1.1-0ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i utouch-frame-tools_1.1.1-0ubuntu1_i386.deb 
Selecting previously deselected package utouch-frame-tools.
(Reading database ... 147433 files and directories currently installed.)
Unpacking utouch-frame-tools (from utouch-frame-tools_1.1.1-0ubuntu1_i386.deb) ...
Setting up utouch-frame-tools (1.1.1-0ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-grail1_1.0.19-0ubuntu2_i386.deb 
(Reading database ... 147439 files and directories currently installed.)
Preparing to replace libutouch-grail1 1.0.19-0ubuntu2 (using libutouch-grail1_1.0.19-0ubuntu2_i386.deb) ...
Unpacking replacement libutouch-grail1 ...
[COLOR="rgb(0, 100, 0)"]**Setting up libutouch-grail1**[/COLOR] (1.0.19-0ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-grail-dev_1.0.19-0ubuntu2_i386.deb 
Selecting previously deselected package libutouch-grail-dev.
(Reading database ... 147439 files and directories currently installed.)
Unpacking libutouch-grail-dev (from libutouch-grail-dev_1.0.19-0ubuntu2_i386.deb) ...
Setting up libutouch-grail-dev (1.0.19-0ubuntu2) ...
root@tab-touch:/home/tab/Downloads# dpkg -i utouch-grail-tools_1.0.19-0ubuntu2_i386.deb 
Selecting previously deselected package utouch-grail-tools.
(Reading database ... 147448 files and directories currently installed.)
Unpacking utouch-grail-tools (from utouch-grail-tools_1.0.19-0ubuntu2_i386.deb) ...
Setting up utouch-grail-tools (1.0.19-0ubuntu2) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis1_2.0.1-0ubuntu1_i386.deb 
(Reading database ... 147453 files and directories currently installed.)
Preparing to replace libutouch-geis1 2.0.1-0ubuntu1 (using libutouch-geis1_2.0.1-0ubuntu1_i386.deb) ...
Unpacking replacement libutouch-geis1 ...
dpkg: dependency problems prevent configuration of libutouch-geis1:
 libutouch-geis1 depends on libx11-xcb1; however:
  Package libx11-xcb1 is not installed.
dpkg: error processing libutouch-geis1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libutouch-geis1
root@tab-touch:/home/tab/Downloads# ls libx11-
ls: cannot access libx11-: No such file or directory
root@tab-touch:/home/tab/Downloads# ls libx11*
libx11-6_1.4.1-5ubuntu1_i386.deb        libx11-dev_1.4.1-5ubuntu1_i386.deb
libx11-6-dbg_1.4.1-5ubuntu1_i386.deb    libx11-xcb1_1.4.1-5ubuntu1_i386.deb
libx11-6-udeb_1.4.1-5ubuntu1_i386.udeb  libx11-xcb1-dbg_1.4.1-5ubuntu1_i386.deb
libx11-data_1.4.1-5ubuntu1_all (1).deb  libx11-xcb-dev_1.4.1-5ubuntu1_i386.deb
libx11-data_1.4.1-5ubuntu1_all.deb
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-6_1.4.1-5ubuntu1_i386.deb 
(Reading database ... 147453 files and directories currently installed.)
Preparing to replace libx11-6 2:1.3.2-1ubuntu3 (using libx11-6_1.4.1-5ubuntu1_i386.deb) ...
Unpacking replacement libx11-6 ...
Setting up libx11-6 (2:1.4.1-5ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-dev_1.4.1-5ubuntu1_i386.deb 
Selecting previously deselected package libx11-dev.
(Reading database ... 147452 files and directories currently installed.)
Unpacking libx11-dev (from libx11-dev_1.4.1-5ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libx11-dev:
 libx11-dev depends on libxau-dev (>= 1:1.0.0-1); however:
  Package libxau-dev is not installed.
 libx11-dev depends on libxdmcp-dev (>= 1:1.0.0-1); however:
  Package libxdmcp-dev is not installed.
 libx11-dev depends on x11proto-core-dev (>= 6.8.99.8-1); however:
  Package x11proto-core-dev is not installed.
 libx11-dev depends on x11proto-input-dev; however:
  Package x11proto-input-dev is not installed.
 libx11-dev depends on x11proto-kb-dev; however:
  Package x11proto-kb-dev is not installed.
 libx11-dev depends on xtrans-dev; however:
  Package xtrans-dev is not installed.
 libx11-dev depends on libxcb1-dev; however:
  Package libxcb1-dev is not installed.
dpkg: error processing libx11-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
[COLOR="red"]Errors[/COLOR] were encountered while processing:
 [COLOR="Red"]libx11-dev[/COLOR]

[COLOR="SeaGreen"]The files now in my Downloads directory are:

libmtdev1_1.1.0-0ubuntu1_i386.deb
libmtdev1-udeb_1.1.0-0ubuntu1_i386.udeb
libmtdev-dev_1.1.0-0ubuntu1_i386.deb
libutouch-evemu1_1.0.4-0ubuntu1_i386.deb
libutouch-evemu1-udeb_1.0.4-0ubuntu1_i386.udeb
libutouch-evemu-dev_1.0.4-0ubuntu1_i386.deb
libutouch-frame1_1.1.1-0ubuntu1_i386.deb
libutouch-frame1-udeb_1.1.1-0ubuntu1_i386.udeb
libutouch-frame-dev_1.1.1-0ubuntu1_i386.deb
libutouch-geis1_2.0.1-0ubuntu1_i386.deb
libutouch-geis-dev_2.0.1-0ubuntu1_i386.deb
libutouch-geis-doc_2.0.1-0ubuntu1_all.deb
libutouch-grail1_1.0.19-0ubuntu2_i386.deb
libutouch-grail1-udeb_1.0.19-0ubuntu2_i386.udeb
libutouch-grail-dev_1.0.19-0ubuntu2_i386.deb
libx11-6_1.4.1-5ubuntu1_i386.deb
libx11-6-dbg_1.4.1-5ubuntu1_i386.deb
libx11-6-udeb_1.4.1-5ubuntu1_i386.udeb
libx11-data_1.4.1-5ubuntu1_all (1).deb
libx11-data_1.4.1-5ubuntu1_all.deb
libx11-dev_1.4.1-5ubuntu1_i386.deb
libx11-xcb1_1.4.1-5ubuntu1_i386.deb
libx11-xcb1-dbg_1.4.1-5ubuntu1_i386.deb
libx11-xcb-dev_1.4.1-5ubuntu1_i386.deb
mtdev-tools_1.1.0-0ubuntu1_i386.deb
utouch_1.1.dsc
utouch_1.1.tar.gz
utouch-evemu-tools_1.0.4-0ubuntu1_i386.deb
utouch-frame-tools_1.1.1-0ubuntu1_i386.deb
utouch-geis-tools_2.0.1-0ubuntu1_i386.deb
utouch-gesturetest_1.0.4-0ubuntu1.debian.tar.gz
utouch-gesturetest_1.0.4-0ubuntu1.dsc
utouch-gesturetest-1.0.4.tar.gz
utouch-grail-tools_1.0.19-0ubuntu2_i386.deb
[/COLOR]

---

### Post by Perfect Storm on 2011-02-24
Try rollback/remove the packages you're installing and try utouch ubuntu PPA instad: [https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch)

---

### Post by openick on 2011-02-24
Dear Artifcial Intelligence :) ,

> **Artificial Intelligence said:**
> Try rollback/remove the packages you're installing and try utouch ubuntu PPA instad: [https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch)

This must have been very, very helpful had I came back to this thread to look for your reply, but fixed on the process already started I have proceeded to go through the dependency issues, one after another, one bringing up another, and a partial log of what I have gone through so far is here

I have two options, 

1. try adding the PPA for the final step, utouch ( haven't found the deb package, but only a tar.gz file, which would require me to make and build, a process I am not tried more than once or twice.

2.  Reverse everything [http://paste.ubuntu.com/571917/](http://paste.ubuntu.com/571917/) 16350 lines of dpkg log in the last two days ! ( :) ) and to through the PPA

What should I do ?  [COLOR="navy"][B]Is there a way of trying out the last step, i.e., just that of installing utouch_1.1.dsc and
utouch_1.1.tar.gz (all dependencies have been installed )[/B][/COLOR]



(Reading database ... 148530 files and directories currently installed.)
Unpacking x11proto-kb-dev (from x11proto-kb-dev_1.0.5-1_all.deb) ...
Setting up x11proto-kb-dev (1.0.5-1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i xtrans-dev_1.2.6-1_all.deb 
Selecting previously deselected package xtrans-dev.
(Reading database ... 148538 files and directories currently installed.)
Unpacking xtrans-dev (from xtrans-dev_1.2.6-1_all.deb) ...
[COLOR="navy"]**Setting up xtrans-dev**[/COLOR] (1.2.6-1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb1-dev_1.7-2_i386.deb 
Selecting previously deselected package libxcb1-dev.
(Reading database ... 148556 files and directories currently installed.)
Unpacking libxcb1-dev (from libxcb1-dev_1.7-2_i386.deb) ...
dpkg: dependency problems prevent configuration of libxcb1-dev:
 libxcb1-dev depends on libxcb1 (= 1.7-2); however:
  Version of libxcb1 on system is 1.5-2.
 libxcb1-dev depends on libpthread-stubs0-dev; however:
  Package libpthread-stubs0-dev is not installed.
dpkg: error processing libxcb1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb1-dev
root@tab-touch:/home/tab/Downloads# dpkg -i libpthread-stubs0-dev_0.3-2_i386.deb 
Selecting previously deselected package libpthread-stubs0-dev.
(Reading database ... 148568 files and directories currently installed.)
Unpacking libpthread-stubs0-dev (from libpthread-stubs0-dev_0.3-2_i386.deb) ...
dpkg: dependency problems prevent configuration of libpthread-stubs0-dev:
 libpthread-stubs0-dev depends on libpthread-stubs0 (= 0.3-2); however:
  Package libpthread-stubs0 is not installed.
dpkg: error processing libpthread-stubs0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpthread-stubs0-dev
root@tab-touch:/home/tab/Downloads# dpkg -i libpthread-stubs0_0.3-2_i386.deb 
Selecting previously deselected package libpthread-stubs0.
(Reading database ... 148573 files and directories currently installed.)
Unpacking libpthread-stubs0 (from libpthread-stubs0_0.3-2_i386.deb) ...
Setting up libpthread-stubs0 (0.3-2) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libpthread-stubs0-dev_0.3-2_i386.deb 
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libpthread-stubs0-dev 0.3-2 (using libpthread-stubs0-dev_0.3-2_i386.deb) ...
Unpacking replacement libpthread-stubs0-dev ...
Setting up libpthread-stubs0-dev (0.3-2) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxau-dev_1.0.6-1_i386.deb 
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libxau-dev 1:1.0.6-1 (using libxau-dev_1.0.6-1_i386.deb) ...
Unpacking replacement libxau-dev ...
Setting up libxau-dev (1:1.0.6-1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb1_1.7-2_i386.deb 
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libxcb1 1.5-2 (using libxcb1_1.7-2_i386.deb) ...
Unpacking replacement libxcb1 ...
Setting up libxcb1 (1.7-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libxdmcp-dev_1.1.0-1_i386
dpkg: error processing libxdmcp-dev_1.1.0-1_i386 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libxdmcp-dev_1.1.0-1_i386
root@tab-touch:/home/tab/Downloads# dpkg -i libxdmcp-dev_1.1.0-1_i386.deb (Reading database ... 148577 files and directories currently installed.)
Preparing to replace libxdmcp-dev 1:1.1.0-1 (using libxdmcp-dev_1.1.0-1_i386.deb) ...
Unpacking replacement libxdmcp-dev ...
Setting up libxdmcp-dev (1:1.1.0-1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libpthread-stubs0-dev_0.3-2_i386.deb 
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libpthread-stubs0-dev 0.3-2 (using libpthread-stubs0-dev_0.3-2_i386.deb) ...
Unpacking replacement libpthread-stubs0-dev ...
Setting up libpthread-stubs0-dev (0.3-2) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb1_1.7-2_i386.deb 
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libxcb1 1.7-2 (using libxcb1_1.7-2_i386.deb) ...
Unpacking replacement libxcb1 ...
Setting up libxcb1 (1.7-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i xtrans-dev_1.2.6-1_all.deb
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace xtrans-dev 1.2.6-1 (using xtrans-dev_1.2.6-1_all.deb) ...
Unpacking replacement xtrans-dev ...
Setting up xtrans-dev (1.2.6-1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-dev_1.4.1-5ubuntu1_i386.deb
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libx11-dev 2:1.4.1-5ubuntu1 (using libx11-dev_1.4.1-5ubuntu1_i386.deb) ...
Unpacking replacement libx11-dev ...
dpkg: dependency problems prevent configuration of libx11-dev:
 libx11-dev depends on libxcb1-dev; however:
  Package libxcb1-dev is not configured yet.
dpkg: error processing libx11-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libx11-dev
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb1-dev_1.7-2_i386.deb
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libxcb1-dev 1.7-2 (using libxcb1-dev_1.7-2_i386.deb) ...
Unpacking replacement libxcb1-dev ...
Setting up libxcb1-dev (1.7-2) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-dev_1.4.1-5ubuntu1_i386.deb
(Reading database ... 148577 files and directories currently installed.)
Preparing to replace libx11-dev 2:1.4.1-5ubuntu1 (using libx11-dev_1.4.1-5ubuntu1_i386.deb) ...
Unpacking replacement libx11-dev ...
[COLOR="navy"]**Setting up libx11-dev**[/COLOR] (2:1.4.1-5ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# ls libx11*
libx11-6_1.4.1-5ubuntu1_i386.deb        libx11-dev_1.4.1-5ubuntu1_i386.deb
libx11-6-dbg_1.4.1-5ubuntu1_i386.deb    libx11-xcb1_1.4.1-5ubuntu1_i386.deb
libx11-6-udeb_1.4.1-5ubuntu1_i386.udeb  libx11-xcb1-dbg_1.4.1-5ubuntu1_i386.deb
libx11-data_1.4.1-5ubuntu1_all (1).deb  libx11-xcb-dev_1.4.1-5ubuntu1_i386.deb
libx11-data_1.4.1-5ubuntu1_all.deb
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-6-dbg_1.4.1-5ubuntu1_i386.deb
Selecting previously deselected package libx11-6-dbg.
(Reading database ... 148577 files and directories currently installed.)
Unpacking libx11-6-dbg (from libx11-6-dbg_1.4.1-5ubuntu1_i386.deb) ...
Setting up libx11-6-dbg (2:1.4.1-5ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-xcb1_1.4.1-5ubuntu1_i386.deb
Selecting previously deselected package libx11-xcb1.
(Reading database ... 148584 files and directories currently installed.)
Unpacking libx11-xcb1 (from libx11-xcb1_1.4.1-5ubuntu1_i386.deb) ...
Setting up libx11-xcb1 (2:1.4.1-5ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads#  dpkg -i libx11-xcb1-dbg_1.4.1-5ubuntu1_i386.deb
Selecting previously deselected package libx11-xcb1-dbg.
(Reading database ... 148589 files and directories currently installed.)
Unpacking libx11-xcb1-dbg (from libx11-xcb1-dbg_1.4.1-5ubuntu1_i386.deb) ...
Setting up libx11-xcb1-dbg (2:1.4.1-5ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-xcb-dev_1.4.1-5ubuntu1_i386.deb
Selecting previously deselected package libx11-xcb-dev.
(Reading database ... 148593 files and directories currently installed.)
Unpacking libx11-xcb-dev (from libx11-xcb-dev_1.4.1-5ubuntu1_i386.deb) ...
[COLOR="navy"]**Setting up libx11-xcb-dev**[/COLOR] (2:1.4.1-5ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i libx11-data_1.4.1-5ubuntu1_all.deb
(Reading database ... 148602 files and directories currently installed.)
Preparing to replace libx11-data 2:1.3.2-1ubuntu3 (using libx11-data_1.4.1-5ubuntu1_all.deb) ...
Unpacking replacement libx11-data ...
Setting up libx11-data (2:1.4.1-5ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis1_2.0.1-0ubuntu1_i386.deb 
(Reading database ... 148602 files and directories currently installed.)
Preparing to replace libutouch-geis1 2.0.1-0ubuntu1 (using libutouch-geis1_2.0.1-0ubuntu1_i386.deb) ...
Unpacking replacement libutouch-geis1 ...
Setting up libutouch-geis1 (2.0.1-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geislibutouch-geis-dev_2.0.1-0ubuntu1_i386.deb
dpkg: error processing libutouch-geislibutouch-geis-dev_2.0.1-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libutouch-geislibutouch-geis-dev_2.0.1-0ubuntu1_i386.deb
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis-dev_2.0.1-0ubuntu1_i386.deb
(Reading database ... 148602 files and directories currently installed.)
Preparing to replace libutouch-geis-dev 1.0.11-0ubuntu1 (using libutouch-geis-dev_2.0.1-0ubuntu1_i386.deb) ...
Unpacking replacement libutouch-geis-dev ...
Setting up libutouch-geis-dev (2.0.1-0ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libutouch-geis-doc_2.0.1-0ubuntu1_all.deb 
Selecting previously deselected package libutouch-geis-doc.
(Reading database ... 148602 files and directories currently installed.)
Unpacking libutouch-geis-doc (from libutouch-geis-doc_2.0.1-0ubuntu1_all.deb) ...
Setting up libutouch-geis-doc (2.0.1-0ubuntu1) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
root@tab-touch:/home/tab/Downloads# dpkg -i utouch-geis-tools_2.0.1-0ubuntu1_i386.deb 
Selecting previously deselected package utouch-geis-tools.
(Reading database ... 148708 files and directories currently installed.)
Unpacking utouch-geis-tools (from utouch-geis-tools_2.0.1-0ubuntu1_i386.deb) ...
[COLOR="navy"]**Setting up utouch-geis-tools**[/COLOR] (2.0.1-0ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i utouch-gesturetest_1.0.4-0ubuntu1_i386.deb
Selecting previously deselected package utouch-gesturetest.
(Reading database ... 148713 files and directories currently installed.)
Unpacking utouch-gesturetest (from utouch-gesturetest_1.0.4-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of utouch-gesturetest:
 utouch-gesturetest depends on libxcb-icccm1 (>= 0.3.6); however:
  Package libxcb-icccm1 is not installed.
dpkg: error processing utouch-gesturetest (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 utouch-gesturetest
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-atom1-dev_0.3.6-1build1_i386.deb 
Selecting previously deselected package libxcb-atom1-dev.
(Reading database ... 148718 files and directories currently installed.)
Unpacking libxcb-atom1-dev (from libxcb-atom1-dev_0.3.6-1build1_i386.deb) ...
Setting up libxcb-atom1-dev (0.3.6-1build1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-icccm1_0.3.6-1build1_i386.deb 
Selecting previously deselected package libxcb-icccm1.
(Reading database ... 148726 files and directories currently installed.)
Unpacking libxcb-icccm1 (from libxcb-icccm1_0.3.6-1build1_i386.deb) ...
dpkg: dependency problems prevent configuration of libxcb-icccm1:
 libxcb-icccm1 depends on libxcb-property1 (>= 0.3.6); however:
  Package libxcb-property1 is not installed.
dpkg: error processing libxcb-icccm1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-icccm1
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-property1_0.3.6-1build1_i386.deb 
Selecting previously deselected package libxcb-property1.
(Reading database ... 148732 files and directories currently installed.)
Unpacking libxcb-property1 (from libxcb-property1_0.3.6-1build1_i386.deb) ...
Setting up libxcb-property1 (0.3.6-1build1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-property1-dev_0.3.6-1build1_i386.deb 
Selecting previously deselected package libxcb-property1-dev.
(Reading database ... 148738 files and directories currently installed.)
Unpacking libxcb-property1-dev (from libxcb-property1-dev_0.3.6-1build1_i386.deb) ...
dpkg: dependency problems prevent configuration of libxcb-property1-dev:
 libxcb-property1-dev depends on libxcb-event1-dev; however:
  Package libxcb-event1-dev is not installed.
dpkg: error processing libxcb-property1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-property1-dev
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-icccm1_0.3.6-1build1_i386.deb 
(Reading database ... 148746 files and directories currently installed.)
Preparing to replace libxcb-icccm1 0.3.6-1build1 (using libxcb-icccm1_0.3.6-1build1_i386.deb) ...
Unpacking replacement libxcb-icccm1 ...
Setting up libxcb-icccm1 (0.3.6-1build1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-icccm1-dev_0.3.6-1build1_i386.deb 
Selecting previously deselected package libxcb-icccm1-dev.
(Reading database ... 148746 files and directories currently installed.)
Unpacking libxcb-icccm1-dev (from libxcb-icccm1-dev_0.3.6-1build1_i386.deb) ...
dpkg: dependency problems prevent configuration of libxcb-icccm1-dev:
 libxcb-icccm1-dev depends on libxcb-property1-dev; however:
  Package libxcb-property1-dev is not configured yet.
dpkg: error processing libxcb-icccm1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-icccm1-dev
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-property1-dev_0.3.6-1build1_i386.deb 
(Reading database ... 148754 files and directories currently installed.)
Preparing to replace libxcb-property1-dev 0.3.6-1build1 (using libxcb-property1-dev_0.3.6-1build1_i386.deb) ...
Unpacking replacement libxcb-property1-dev ...
dpkg: dependency problems prevent configuration of libxcb-property1-dev:
 libxcb-property1-dev depends on libxcb-event1-dev; however:
  Package libxcb-event1-dev is not installed.
dpkg: error processing libxcb-property1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-property1-dev
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-event1-dev_0.3.6-1build1_i386.deb 
Selecting previously deselected package libxcb-event1-dev.
(Reading database ... 148754 files and directories currently installed.)
Unpacking libxcb-event1-dev (from libxcb-event1-dev_0.3.6-1build1_i386.deb) ...
Setting up libxcb-event1-dev (0.3.6-1build1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-property1-dev_0.3.6-1build1_i386.deb 
(Reading database ... 148762 files and directories currently installed.)
Preparing to replace libxcb-property1-dev 0.3.6-1build1 (using libxcb-property1-dev_0.3.6-1build1_i386.deb) ...
Unpacking replacement libxcb-property1-dev ...
Setting up libxcb-property1-dev (0.3.6-1build1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-icccm1-dev_0.3.6-1build1_i386.deb
(Reading database ... 148762 files and directories currently installed.)
Preparing to replace libxcb-icccm1-dev 0.3.6-1build1 (using libxcb-icccm1-dev_0.3.6-1build1_i386.deb) ...
Unpacking replacement libxcb-icccm1-dev ...
Setting up libxcb-icccm1-dev (0.3.6-1build1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i libxcb-icccm1-dev_0.3.6-1build1_i386.deb
(Reading database ... 148762 files and directories currently installed.)
Preparing to replace libxcb-icccm1-dev 0.3.6-1build1 (using libxcb-icccm1-dev_0.3.6-1build1_i386.deb) ...
Unpacking replacement libxcb-icccm1-dev ...
Setting up libxcb-icccm1-dev (0.3.6-1build1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i utouch-gesturetest_1.0.4-0ubuntu1_i386.deb
(Reading database ... 148762 files and directories currently installed.)
Preparing to replace utouch-gesturetest 1.0.4-0ubuntu1 (using utouch-gesturetest_1.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement utouch-gesturetest ...
[COLOR="navy"]**Setting up utouch-gesturetest**[/COLOR] (1.0.4-0ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads# dpkg -i libmtdev1_1.1.0-0ubuntu1_i386.deb 
(Reading database ... 148762 files and directories currently installed.)
Preparing to replace libmtdev1 1.1.0-0ubuntu1 (using libmtdev1_1.1.0-0ubuntu1_i386.deb) ...
Unpacking replacement libmtdev1 ...
Setting up libmtdev1 (1.1.0-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@tab-touch:/home/tab/Downloads# dpkg -i libmtdev-dev_1.1.0-0ubuntu1_i386.deb 
(Reading database ... 148762 files and directories currently installed.)
Preparing to replace libmtdev-dev 1.1.0-0ubuntu1 (using libmtdev-dev_1.1.0-0ubuntu1_i386.deb) ...
Unpacking replacement libmtdev-dev ...
Setting up libmtdev-dev (1.1.0-0ubuntu1) ...
root@tab-touch:/home/tab/Downloads# dpkg -i mtdev-tools_1.1.0-0ubuntu1_i386.deb 
Selecting previously deselected package mtdev-tools.
(Reading database ... 148762 files and directories currently installed.)
Unpacking mtdev-tools (from mtdev-tools_1.1.0-0ubuntu1_i386.deb) ...
[COLOR="Navy"]**Setting up mtdev-tools**[/COLOR] (1.1.0-0ubuntu1) ...
Processing triggers for man-db ...
root@tab-touch:/home/tab/Downloads#

---

### Post by openick on 2011-02-26
Hello

I want to know how to make install /Downloads/utouch_1.1.tar.gz  (there is also a file called utouch_1.1.dsc )  

All dependencies have been installed already by adding deb packages from natty.

Followed instructions on page [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) to install build essential and checkinstall and cvs subversion git-core mercurial

but don't seem to find a 'source' directory or 'readme' within the extracted files ( utouch_1.1.tar.gz )

Thank you

---

### Post by Perfect Storm on 2011-02-26
utouch is a meta-package, which means it's job is to grab diffrent .deb files in the repositories.
[https://launchpad.net/ubuntu/+source/utouch/1.1](https://launchpad.net/ubuntu/+source/utouch/1.1)

> 
**utouch: A meta-package to install gesture libraries and tools**

This package provides a development environment for building gesture aware
 applications. It installs mtdev, utouch-grail, utouch-gesturetest, and
 utouch-geis, and their related development headers and test tools.


You know that utouch (and its packages are available in Ubuntu Software Center).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=184547&stc=1&d=1298739419[/IMG]

---

### Post by openick on 2011-02-26
> **Artificial Intelligence said:**
> utouch is a meta-package, which means it's job is to grab diffrent .deb files in the repositories.
[https://launchpad.net/ubuntu/+source/utouch/1.1](https://launchpad.net/ubuntu/+source/utouch/1.1)

Dear AI

Went there, found the package utouch_1.1_all.deb, the dpkp process was brief, hardly 15 seconds, no errors, 

dpkg -i utouch_1.1_all.deb 
Selecting previously deselected package utouch.
(Reading database ... 148768 files and directories currently installed.)
Unpacking utouch (from utouch_1.1_all.deb) ...
Setting up utouch (1.1) ...
root@tab-touch:/home/tab/Downloads# utouch
No command 'utouch' found, did you mean:
 Command 'ktouch' from package 'ktouch' (main)
 Command 'touch' from package 'coreutils' (main)
utouch: command not found

[IMG]http://www.flickr.com/photos/59988283@N05/5478913923/[/IMG]

root@tab-touch:/home/tab/Downloads# [COLOR="Teal"]**apt-get check**[/COLOR]
[COLOR="Red"][B]Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing mlocate (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.[/B][/COLOR]

The errors in red occurred after the first restart after all the earlier dpkg processes

[QUOTE]You know that utouch (and its packages are available in Ubuntu Software Center).

No, it does not show up. I have 10.04, have [COLOR="Teal"]canonical lucid partner, canonical lucid partner source code, deebian wheezy, chase douglas mutitouch, utouch-team [/COLOR]- all added to the software center repositories, but still it does not show up. 

Quite possibly because the [COLOR="red"]software center hangs[/COLOR] after adding repositories while updating. May be something to do with the error in red / attached picture ?

What should I do?

---

### Post by Perfect Storm on 2011-02-26
ah! The 1.1 version is available in Ubuntu 10.10. 

It may that all the stuff that is needed is first available in Ubuntu 10.10.

Sorry I can't be more help here.

---

### Post by openick on 2011-02-28
> **Artificial Intelligence said:**
> ah! The 1.1 version is available in Ubuntu 10.10. 

It may that all the stuff that is needed is first available in Ubuntu 10.10.

Sorry I can't be more help here.

Tried 10.10 first, before coming back to 10.04.

Now, I will erase 10.04, install 10.10 and see if there is a way out.

Thanks.

---

