---
title: "Netgear WG111T (wireless USB adapter) + ndiswrapper"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by n00b@linux on 2007-01-07
I have been around the houses on this one for a week now without any joy.

I know about [the ndiswrapper Edgy problem]("http://https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983") and I've _un_installed ndiswrapper-utils-1.1 and installed ndiswrapper-utils-1.8 as per [this community doc]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29").

I checked [the list of supported devices at the ndiswrapper.sourceforge.net mediawiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N") and saw that my device (Netgear WG111T - **which has an Atheros chipset**) is supported (see the second '4.' under 'N' of the list).

So I ndiswrapper-1.8'd the windoze modules and got the following:```
n00b@ubuntu:~$ ndiswrapper -l
Installed drivers:
athfmwdl                driver installed
netwg11t                driver installed, hardware present
```I then modprobed ndiswrapper and it worked!  Or so I thought.  

When I rebooted and modprobed again, I was out of luck.  When I double checked the installed drivers I saw this:```
n00b@ubuntu:~$ ndiswrapper -l
Installed drivers:
athfmwdl                driver installed, hardware present 
netwg11t                driver installed
```Reboot after reboot I soon discovered that my WG111T works when netwg11t detects the hardware, but is totally shagged when athfmwdl detects it and that this appears to be a completely random event.

Looking into this further I also discovered found that:

(a) my device's usbid is 1385:425_1_ and NOT 1385:4250 as per the abovementioned entry in the ndiswrapper.sourceforge.net mediawiki list.  However, this doesn't appear to be a major problem as I did get it to work, albeit briefly.
(b) version 1.23 of ndiswrapper (from sourceforge) has the following in its changelog:> Version 1.23 2006-08-10
=======================    
* Bug fixes to recent changes in 64-bit driver support.
* ZyDas ZD1211 driver uses interrupt-out URBs, so set them up properly.
*** Bug fixes to Atheros USB driver support**.The upshot of all of this is that ndiswrapper DOES support my USB wireless adapter but the binary version in the Ubuntu repos DOESN'T.   So I figured I would try and compile ndiswrapper from source.  

Now I'm not a developer and I don't know anything about C++, but I can follow the instructions in a README and an INSTALL and I can follow the code in a Makefile and tie it up with the errors I get when I compile.  But I can't interpret what I should do to fix it.

The errors I'm getting when I try to compile from source are all 'No such file or directory' and relate to this list of files (taken from the offending Makefile):```
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>
#include <string.h>
#include <libgen.h>
#include <sys/mman.h>
#include <sys/types.h>
#include <sys/ioctl.h>
#include <sys/stat.h>
#include <unistd.h>
#include <fcntl.h>
#include <limits.h>
#include <ctype.h>
#include <dirent.h>
#include <syslog.h>
#include <stdlib.h>
#include <linux/major.h>
#include <linux/ioctl.h>
```Can anyone tell me how I can fix this so that I can compile a version of ndiswrapper that supports my hardware?   Alternatively, can anyone point me to a .deb package for ndiswrapper that is at least version 1.23?

---

### Post by teaker1s on 2007-01-07
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

not for your device but it will guide you through the basics and controlling wireless

---

### Post by n00b@linux on 2007-01-07
Thanks teaker1s.  You are a Godsend.  I followed the link and got ndiswrapper-1.33 installed.  My Netgear WG111T USB wireless adapter is now working without fail.  Thanks once again.  I'm going to add the link you provided to my sig so that others can compile the latest ndiswrapper!

---

