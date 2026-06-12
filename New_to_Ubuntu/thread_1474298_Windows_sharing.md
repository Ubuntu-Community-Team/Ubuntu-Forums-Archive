---
title: "Windows sharing"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by HandleHere on 2010-05-05
After a miserable attempt with Gentoo, I installed Ubuntu 10.04 tonight.  Things are going much better now, however, after searching for a while I still have an unresolved sharing problem.  When attempting to share a folder to be accessed by other LAN computers I get the following error: "'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error."  Samba returns the following: 

Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[Wed May  5 22:07:31 2010 CDT, 0 smbd/server.c:285:binary_smbd_main()]
samba version 4.0.0alpha9-GIT-9733816 started.

Anybody know the fix for this one?  Thanks!

---

### Post by Cowboybebop79 on 2010-05-06
Check if you have the package smbfs on your installation. I had a setup mounting three sections of my NAS at boot by updating the fstab.config on 9.10 karmic after installing 10.04 and updating my fstab nothing would work until I had installed the smbfs package.

either open synaptic package manager and search for "smbfs" synaptic is in administration menu.
 
or open terminal
and paste this and hit enter

```
sudo apt-get install smbfs
```

Hope this helps

---

