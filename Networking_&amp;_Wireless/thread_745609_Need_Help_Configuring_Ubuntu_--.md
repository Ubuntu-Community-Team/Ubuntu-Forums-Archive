---
title: "Need Help Configuring Ubuntu --"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by cuervo73 on 2008-04-05
Hi,

your boot scripts from the caucho website were not written for a Ubuntu/Debian filesystem setup.  It looks more like the RedHat/Fedora style as they use the intermediate directory "rc.d" to contain the other run level subsirectories: rc2.d, rc3.d, rc5.d and init.d

So, just edit the directory path and remove all the occurrences of the subdirectory rc.d/...
For example, the step 4 path would appear like this after your editing:

4. "ln -s /usr/local/resin/bin/resin-a.sh /etc/rc3.d/S86resin-a"

That should fix you for Ubuntu.

HTH,

cuervo

---

