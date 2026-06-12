---
title: "[SOLVED] Wireless card stopped working - tries to connect but never manages it!"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by spleencheesemonkey on 2008-01-25
Hi all.

Had my wireless card working for the last 6 months or so with no problems using network manager until recently:
I used to keep my pc connected to the router by ethernet but occasionally would tidy the living room to get rid of the cable draped accross the floor and it would automatically go to wireless connection.  The other day (I presume after an update) it would not connect wirelessly after removing the ethernet connection.  It tries, prompts for the network encryption password which I enter but it never connects.
I have looked at /var/log/syslog which shows some interesting entries:

Jan 25 20:22:58  NetworkManager: <info>  Old device 'ra0' activating, won't change. 
Jan 25 20:23:24  kernel: [ 8639.240000] ra0: RX WEP frame with unknown keyidx 1 (A1=ff:ff:ff:ff:ff:ff A2=00:90:d0:e4:19:61 A3=00:14:7f:e4:19:61)

Whether these are of any use or not in helping to identify the problem, I am not sure.  If someone could find the time to help me solve this problem I'd be very grateful.

Please feel free to request outputs of terminal commands that are required to help identify drivers/hardware etc - I'm not really sure where to start.

Many thanks in advance.

---

### Post by spleencheesemonkey on 2008-01-26
25 views an no suggestions? :(

---

### Post by spleencheesemonkey on 2008-01-28
Hmm,

Seems all I needed to do was boot into Windows, connect via wireless, then reboot into Gutsy and it worked.

Most strange.

---

### Post by Henrywantstobeapenguin on 2008-01-28
How do I add the SOLVED tag to my threads? Thanks

Henry

---

### Post by spleencheesemonkey on 2008-01-28
There's a link towards the top of the page called "Thread tools".  You'll find it under that menu. :)

---

