---
title: "Sagem Modem Problem"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by adil_uk on 2007-08-09
Hi

I'm having problem connecting to my ISP. It seems to me a Authentication problem.

Aug  9 14:12:14 pppd[9783]: Remote message: Request Denied
Aug  9 14:12:14  pppd[9783]: PAP authentication failed
Aug  9 14:12:20  pppd[9783]: Connection terminated.
Aug  9 14:12:20  pppd[9783]: Modem hangup
Aug  9 14:12:50  pppd[9783]: Using interface ppp0
Aug  9 14:12:50  pppd[9783]: Connect: ppp0 <--> 0.38
Aug  9 14:13:07  pppd[9783]: Remote message: Request Denied
Aug  9 14:13:07  pppd[9783]: PAP authentication failed
Aug  9 14:13:13  pppd[9783]: Connection terminated.
Aug  9 14:13:13  pppd[9783]: Modem hangup

I made sure pap-secrets file contain the correct  password yet I can't log in to the ISP.

the modem is operational....

[ueagle-atm] using iso mode
[ 6439.748000] usb 1-2: [ueagle-atm] (re)booting started
[ 6441.676000] usb 1-2: [ueagle-atm] ATU-R firmware version : 44e2ea17
[ 6441.724000] usb 1-2: [ueagle-atm] Modem started, waiting synchronization
[ 6454.884000] usb 1-2: [ueagle-atm] modem operational

Am I missing something here?

thanks in advance.

---

### Post by adil_uk on 2007-08-10
Problem Solved

!!!! 

for future reference make sure the file pap-secrets is in /etc/ppp ... thats all.

---

