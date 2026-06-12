---
title: "Authentication failure - Speedtouch USB"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by peterthebike on 2005-11-16
I have used the instructions in [http://www.ubuntuforums.org/showthread.php?t=44763]("http://www.ubuntuforums.org/showthread.php?t=44763") to setup my Speedtouch USB modem.

Authentication fails though:
> Nov 16 14:53:50 localhost usb.agent[10395]:      speedtch: already loaded
Nov 16 14:53:50 localhost pppd[10440]: Plugin pppoatm.so loaded.
Nov 16 14:53:50 localhost pppd[10441]: pppd 2.4.3 started by root uid 0
Nov 16 14:53:51 localhost usb.agent[10431]:      speedtch: already loaded
Nov 16 14:53:51 localhost pppd[10520]: Plugin pppoatm.so loaded.
Nov 16 14:53:51 localhost usb.agent[10434]:      speedtch: already loaded
Nov 16 14:53:51 localhost pppd[10567]: Plugin pppoatm.so loaded.
Nov 16 14:53:51 localhost usb.agent[10395]:      speedtouch: loaded successfully
Nov 16 14:53:51 localhost pppd[10521]: pppd 2.4.3 started by root uid 0
Nov 16 14:53:51 localhost pppd[10568]: pppd 2.4.3 started by root uid 0
Nov 16 14:53:51 localhost usb.agent[10431]:      speedtouch: loaded successfully
Nov 16 14:53:52 localhost usb.agent[10434]:      speedtouch: loaded successfully
Nov 16 14:53:57 localhost pppd[10521]: Exit.
Nov 16 14:53:57 localhost pppd[10441]: Exit.
Nov 16 14:53:57 localhost pppd[10568]: Using interface ppp0
Nov 16 14:53:57 localhost pppd[10568]: Connect: ppp0 <--> 0.38
Nov 16 14:54:12 localhost pppd[10568]: Remote message: Authentication failed
Nov 16 14:54:12 localhost pppd[10568]: Connection terminated.


I see some threads refer to problems with libatm1. Is my problem related to this? :???:

When I first installed Breezy I was using an external modem on dial-up.

Using dual-boot I can connect under WinXP.

---

### Post by peterthebike on 2005-11-16
I forgot to add the @abcd.com to the username in chap-secrets and pap-secrets!

Only wasted a day to find what I should have got right in the first place. :cry:

---

### Post by Gallows on 2006-03-19
I feel your pain brother

---

