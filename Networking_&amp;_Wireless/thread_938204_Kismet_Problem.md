---
title: "Kismet Problem"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by TurboPotato on 2008-10-04
Hello,

I've been having a heck of a problem trying to set up kismet on my dell laptop with a ubiquiti card.  I keep getting the same message but I don't know where to go from here.

alex@alex-laptop:/usr/local/etc$ sudo kismet
[sudo] password for alex: 
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to alex (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'madwifi_g' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}


any help?

Thanks,
TurboPotato

---

