---
title: "How to run Thin Client Manager (prev. &quot;Student Control Panel&quot;)"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by eugeneccampbell on 2008-11-26
Edubuntu 8.10 LTSP -- all installed OK, client terminals up and running, but how do I access the Thin Client Manager? I've see reference to it as the new name in 7.04 for a completely reworked Student Control Panel in Dapper. I've seen instructions to access it from the System --> Administration menu and I've seen explanations of what it does once it is up and running. But my installation has nothing under System --> Administration. There is no mention of how to get it running anywhere on my system that I can find (or on the net) -- only how to use it after it while it is running and what happens the first time it is run. For example:

[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-tcm.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-tcm.html)

Searching in Synaptic shows "python-tcm" already installed. Here's the result of a locate:

~$ locate tcm
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/tcm825x.ko
/lib/modules/2.6.24-21-generic/kernel/drivers/media/video/tcm825x.ko
/opt/ltsp/i386/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/tcm825x.ko
/usr/lib/python2.5/site-packages/studentcontrolpanel/ltcm.py
/usr/lib/python2.5/site-packages/studentcontrolpanel/ltcm.pyc
/usr/lib/python2.5/site-packages/studentcontrolpanel/tcmplugins.py
/usr/lib/python2.5/site-packages/studentcontrolpanel/tcmplugins.pyc
/usr/share/doc/python-tcm
/usr/share/doc/python-tcm/changelog.Debian.gz
/usr/share/doc/python-tcm/copyright
/usr/share/pyshared/studentcontrolpanel/ltcm.py
/usr/share/pyshared/studentcontrolpanel/tcmplugins.py
/usr/share/pyshared-data/python-tcm
/usr/src/linux-headers-2.6.24-19/drivers/media/video/tcm825x.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/video/tcm825x.h
/usr/src/linux-headers-2.6.24-21/drivers/media/video/tcm825x.h
/usr/src/linux-headers-2.6.24-21-generic/include/config/video/tcm825x.h
/var/lib/dpkg/info/python-tcm.list
/var/lib/dpkg/info/python-tcm.md5sums
/var/lib/dpkg/info/python-tcm.postinst
/var/lib/dpkg/info/python-tcm.preinst
/var/lib/dpkg/info/python-tcm.prerm
--------------------------------------------------
How can I run this program so I can begin to control the clients? Is is supposed to be on my System menu under Administration, and if so, how do I place it there? I'm not far beyond newbie so please speak slowly :-)

---

### Post by palitone on 2008-12-01
Hi there Eugene...im having problems with my LTSP. I used a Ubuntu 8.10 Alternate CD and on boot I press F4 and selected Install an LTSP server. Ive installed it and now i have 1 thinclient trying to connect but no luck. It has a PXE lan card when it boots the following displays

DHCP MAC ADDR: XX XX XX XX XX XX
PXE-EA1: No PXE server found, using standard boot file.
IP ADD: 192.168.0.20
PXE-E32: TFTP open timeout
PXE-E32: TFTP open timeout
PXE-MOF: Exiting LANDesk service Agent
DISK BOOT FAILURE, INSERT SYSTEM DISK & PRESS ENTER

Nothing happend afterwards....can you please help me and guide me the processes how you installed LTSP. Ive followed the guide on how to install it but tried the F4 and the manual install but still the same....Thanks in advance.

---

### Post by bluman on 2009-03-26
Hi eugeneccampbell, did you (or anyone else) work out how to access the Thin Client Manager on Edubuntu 8.10? I have a fresh install and do not see this in any of the desktop menus. My thin clients are booting and logging in correctly. Sound works out of the box also.

Please help.

Regards
Mark

---

### Post by bluman on 2009-03-28
I found the solution to this problem. Ubuntu 810 does not install Thin Client Manager by default. 

sewer-monkey had posted the answer in the linuxquestions forum at this address.
[http://www.linuxquestions.org/questions/linux-server-73/how-to-run-thin-client-manager-prev.-student-control-panel-686249/](http://www.linuxquestions.org/questions/linux-server-73/how-to-run-thin-client-manager-prev.-student-control-panel-686249/)

The package must be installed seperately. I used apt-get as follows.

sudo apt-get install thin-client-manager-gnome

To access the Thin Client Manager you must run it from the command prompt with 

sudo student-control-panel

I hope this helps others in the future.

---

### Post by ilke42 on 2011-01-24
I have the same problem even when I start like you said.
I will try server restart, then search for other solution.

---

