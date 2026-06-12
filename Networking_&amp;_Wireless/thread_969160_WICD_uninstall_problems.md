---
title: "WICD uninstall problems?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by 1337yit on 2008-11-03
I'm having a spot of trouble getting back to the normal network-manager from wicd. I got wicd in hardy, but I tried the new network-manager on a live CD, and like it much more. I try a "sudo apt-get remove wicd" and this is the response:

```
sudo apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1774kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 136321 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
update-rc.d: warning: /etc/init.d/wicd missing LSB style header
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm kind of a newbie, so any help is greatly appreciated. I have the network-manager .deb file on my computer, so I don't quite know what's going wrong.

---

### Post by imdano on 2008-11-03
See [this thread](http://wicd.net/punbb/viewtopic.php?id=187).

---

