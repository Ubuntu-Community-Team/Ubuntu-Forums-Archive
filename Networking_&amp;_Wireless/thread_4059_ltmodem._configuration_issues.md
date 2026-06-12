---
title: "ltmodem. configuration issues"
date: 2004-11-11
forum: Networking &amp; Wireless
---

### Post by allen on 2004-11-11
ok i've managed to install the drivers by making a deb file for my....

Class 0780: 11c1:044a   Communication controller: Lucent Microelectronics F-1156IV WinModem (V90, 56KFlex) (rev 01)

.... and the modules are loaded at boot-time. i can through network admin click activate and it will dial the isp and connect (audibly). however, the tick disappears in the active row around 20ms after i click activate. before the noise from the dial tone even pops up and it continues to connect. not only is the active checkbox not ticked nothing is loaded when going into firefox and trying to go to [www.google.com](www.google.com). (i've tried just by googles ip too).

wvdial does similar results. it dials up and has problems with 'pppd'. i'll post an error msg in a moment. 

pon fails to ring after correctly setting it up through pppconfig and adding myself to the dip group.

ps. connecting though ethernet connection to brothers windows box. this makes me feel dirty and its power inefficient.

suse 9.1 managed to connect using my modem so i know it works in linux. hopefully i can get it working as i prefer ubuntu so much over windows and suse9.1.

---

### Post by az on 2004-11-11
After you do 
sudo pon
would you post the result from
sudo tail -f /var/log/messages

---

### Post by allen on 2004-11-11
Nov 11 19:48:40 localhost chat[27277]: expect (phone)
Nov 11 19:48:40 localhost chat[27277]: ^M
Nov 11 19:49:12 localhost pppd[25968]: Terminating on signal 15.
Nov 11 19:49:14 localhost pppd[25968]: Exit.
Nov 11 19:49:21 localhost pppd[27295]: pppd 2.4.2 started by root, uid 0
Nov 11 19:49:22 localhost chat[27296]: abort on (BUSY)
Nov 11 19:49:22 localhost chat[27296]: abort on (NO CARRIER)
Nov 11 19:49:22 localhost chat[27296]: abort on (VOICE)
Nov 11 19:49:22 localhost chat[27296]: abort on (NO DIALTONE)
Nov 11 19:49:22 localhost chat[27296]: send (ATZW2^M)
Nov 11 19:49:22 localhost chat[27296]: expect (OK)
Nov 11 19:49:23 localhost chat[27296]: ATZW2^M^M
Nov 11 19:49:23 localhost chat[27296]: OK
Nov 11 19:49:23 localhost chat[27296]:  -- got it
Nov 11 19:49:23 localhost chat[27296]: send (ATDT<put^M)
Nov 11 19:49:23 localhost chat[27296]: expect (phone)
Nov 11 19:49:23 localhost chat[27296]: ^M
Nov 11 19:50:08 localhost chat[27296]: alarm
Nov 11 19:50:08 localhost chat[27296]: Failed

--repeats till poff when it then shows as expected --

Nov 11 19:51:09 localhost pppd[27295]: Terminating on signal 15.
Nov 11 19:51:09 localhost pppd[27295]: Exit.

---

### Post by zenwhen on 2004-11-16
Have you tried gnome-ppp?

---

### Post by pazu on 2004-11-29
The same is happening to me. wvdial/pon/gnome-ppp/whatever dials, I can hear the connection noise, but the CONNECT answer never comes, and the dialing times out. The same modem used to work fine under SuSE 9.1, and also works fine under Windows XP. Has anyone found a possible solution to this problem?

---

### Post by conekg on 2004-12-07
I have completely the same problem.

---

### Post by az on 2004-12-07
I think the driver is buggy.  I do not own the hardware, but someone I know just told me that it does not work on his machine.  On the linmodems.org site for the ltmodem, the debian package problems in the source are supposed to be fixed, but I cannot get them to work.  I will contact the maintainer...

If I can get it to build, I will update the link in the howto I made...

[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)

---

