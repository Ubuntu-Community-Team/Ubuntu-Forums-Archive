---
title: "Problem with kismet, ipw2100 and ubuntu 6.10"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Etig0L on 2007-02-12
I have installed version Kismet 2007.01.R1 and it does not detect module ipw2100.

gabriel@thinki:~$ kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to gabriel (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'ipw2100' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

gabriel@thinki:~$ lsmod | grep ipw
ipw2100                75828  0 
ieee80211              35272  1 ipw2100

Not that this happening, that somebody helps me, thanks!!

---

### Post by XploD on 2007-04-11
I've got the same problem. Help anyone?

---

