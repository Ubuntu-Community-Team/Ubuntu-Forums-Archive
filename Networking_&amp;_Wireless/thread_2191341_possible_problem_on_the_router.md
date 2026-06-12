---
title: "possible problem on the router"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by kristal2 on 2013-12-02
Hello to everyone. Hope someone help me with a lil problem.
I have ubuntu 10.04 router. It works fine, but sometimes i had to reload it because the internet in my network was dissapearing. So once i rebooted it through ssh, the internet didn't appeared, and i couldn't connect to the router through ssh again. I connected a monitor and saw some errors.. It was still rebooting...
So the following errors are:
_____
Stopping flow-capture: flow-capture.
Shutdown nfcapd: (eth0) [no collector].
Shutdown nfsend: Use of uninitialized value $pid in scalar chomp at /srv/nfsen/bexec/NfSenRC.pm line 269.
Use of uninitialized value $pid in concatenation (.) or string at /srv/nfsen/exec/NfSenRC.pm line 271.
[] Use of uninitialized value $pid in kill at /srv/nfsen/libexec/NfSenRC.pm line 272.
Can't signal nfsend: at /srv/nfsen/libexec/NfSenRC.pm line 276.
init:Re-executing /sbin/init.......................................................................................................................
.............................................................................................................................................................
.............................................................................................................................................................
.............................................................................................................................................................
.............................. 
______
and after 5-10 minutes it reboots...
I was looking for some familiar errors in the internet but couldn't find smth

---

