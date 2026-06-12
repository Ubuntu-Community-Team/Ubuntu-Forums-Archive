---
title: "Trouble Installing OpenOffice 3"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by kogger on 2009-02-11
I'm trying to install OpenOffice 3. I followed the [instructions](http://download.openoffice.org/common/instructions.html#linux) on the open office site, but when attempting step 6 I get this:

```
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_11-fcs.i586
	/bin/cat is needed by jre-1.6.0_11-fcs.i586
	/bin/cp is needed by jre-1.6.0_11-fcs.i586
	/bin/gawk is needed by jre-1.6.0_11-fcs.i586
	/bin/grep is needed by jre-1.6.0_11-fcs.i586
	/bin/ln is needed by jre-1.6.0_11-fcs.i586
	/bin/ls is needed by jre-1.6.0_11-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_11-fcs.i586
	/bin/mv is needed by jre-1.6.0_11-fcs.i586
	/bin/pwd is needed by jre-1.6.0_11-fcs.i586
	/bin/rm is needed by jre-1.6.0_11-fcs.i586
	/bin/sed is needed by jre-1.6.0_11-fcs.i586
	/bin/sort is needed by jre-1.6.0_11-fcs.i586
	/bin/touch is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_11-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_11-fcs.i586
	/bin/sh is needed by jre-1.6.0_11-fcs.i586
	libfreetype.so.6 is needed by ooobasis3.0-core04-3.0.1-9379.i586
	libgnomevfs-2.so.0 is needed by ooobasis3.0-gnome-integration-3.0.1-9379.i586
	libgconf-2.so.4 is needed by ooobasis3.0-gnome-integration-3.0.1-9379.i586
	/bin/sh is needed by openoffice.org3-dict-en-3.0.1-9379.i586
	/bin/sh is needed by openoffice.org3-dict-es-3.0.1-9379.i586
	/bin/sh is needed by openoffice.org3-dict-fr-3.0.1-9379.i586
```
Any idea how to get it installed?

---

### Post by sleepyjon on 2009-02-11
What version of ubuntu are you running?

If you're running 8.10 this guide worked for me:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by kogger on 2009-02-11
Yeah, I'm on 8.10, and the guide worked. Thanks. =)

---

### Post by gemmala on 2009-02-11
I'm trying this - did try following the guide, but that ended up uninstalling Open Office, it seemed.  Perhaps because I'm running 8.04?  In any case, having done my best to remove all Open Office files from my system so I could go for a clean install, when I reach step 6 of the installation procedure I get:

rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

Any ideas?

---

### Post by howefield on 2009-02-11
Looks like you are trying to install rpm packages instead of deb packages which is what Ubuntu uses. You can convert rpm packages using a program called Alien but it would be a lot easier to use the link that sleepjon provided. It is the easiest way.

---

