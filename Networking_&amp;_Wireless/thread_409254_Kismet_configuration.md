---
title: "Kismet configuration"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by colinireland on 2007-04-14
Could anybody tell me how I can get kismet to run.
Im using Dapper and installed the *.deb package of kismet. heres the output i recieved when i ran it.

root@Niloc:/etc/kismet# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw2200' in source 'ipw2200,eth1,INTEL'
root@Niloc:/etc/kismet#    

I edited the config file with my suid, source, interface etc.

Any help would be greatly appricated

---

### Post by Mr Squiddy on 2007-04-14
Instead of 'ipw2200,eth1,INTEL' try 'ipw2200,eth1,ATHEROS'.  This worked for me.

---

### Post by colinireland on 2007-04-14
Changed the source as you said but got a similar output.

root@Niloc:/etc/kismet# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw2200' in source 'ipw2200,eth1,ATHEROS'
root@Niloc:/etc/kismet#

Any more ideas on how I can rectify this?
Cheers

---

### Post by nukie77 on 2007-04-16
i use ipw2200,eth1,ipw2200 and it will at least start up.

---

