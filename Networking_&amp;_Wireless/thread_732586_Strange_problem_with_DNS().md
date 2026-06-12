---
title: "Strange problem with DNS(?)"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by kttshin on 2008-03-23
I use Kubuntu gutsy gibbon. It seems, I succesfully setuped USB modem Ericcson HM120dp...

(eciadsl-usermode + rp-pppoe)
[EciAdsl 1/5] Setting up USB support...
Preliminary USB device filesystem is OK
[EciAdsl 2/5] Uploading firmware...
Warning: firmware seems to be already loaded
Check that your modem is OFF before running eciadsl-start (if modem is
powered on, then unplug/replug it)
[EciAdsl 3/5] Synchronization...
OK eciadsl-synch: success                                                           
Synchronization successful
[EciAdsl 4/5] Connecting to provider...
Connection successful
[EciAdsl 5/5] Setting up route table...
Waiting for tap0... 

After I initialize pppoe:

maremeco@testare:~$ sudo pppoe-start
pppoe-start: There already seems to be a PPPoE connection up (PID 11427)
maremeco@testare:~$ sudo pppoe-stop
Killing pppd (14228)
Killing pppoe-connect (11427)
maremeco@testare:~$ sudo pppoe-start
. Connected!

ifconfig shows eth0, lo, tap0 and ppp0 interfaces.
plog shows:

Mar 22 22:14:54 testare pppd[17482]: pppd 2.4.4 started by root, uid 0
Mar 22 22:14:54 testare pppd[17482]: Using interface ppp0
Mar 22 22:14:54 testare pppd[17482]: Connect: ppp0 <--> /dev/pts/5
Mar 22 22:14:56 testare pppd[17482]: PAP authentication succeeded
Mar 22 22:14:56 testare pppd[17482]: local  IP address X.X.X.X
Mar 22 22:14:56 testare pppd[17482]: remote IP address X.X.X.X

I can ping remote hosts, and use telnet as well.
But when I try to open a website, tap0 and ppp0 interfaces imidiately disapear.

Mar 22 22:24:01 testare pppd[17482]: Modem hangup
Mar 22 22:24:01 testare pppd[17482]: Connection terminated.
Mar 22 22:24:01 testare pppd[17482]: Exit.

/etc/resolv.conf has my provider dns servers list.

Tried various iptables configurations, but it didn't work.
even iptables -F didn't help.
Maybe the problem hides somethere in the kernel configurations?

---

