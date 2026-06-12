---
title: "modem help (with logs)"
date: 2005-03-24
forum: Networking &amp; Wireless
---

### Post by pugrit on 2005-03-24
i think this should be here. sorry for the other post 
this is the command i did and its corresponding logs.

**********

pugrit@DigitalFart:~ $ sudo pon provider

Mar 24 10:04:00 localhost pppd[3755]: pppd 2.4.2 started by root, uid 0

Mar 24 10:04:02 localhost pppd[3755]: Exit.

**********

pugrit@DigitalFart:~ $ sudo wvdial

--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

**********

computer
system configuration
networking
modem port (/dev/modem)


Mar 24 10:16:07 localhost pppd[5150]: pppd 2.4.2 started by root, uid 0
Mar 24 10:16:08 localhost pppd[5150]: Serial connection established.
Mar 24 10:16:08 localhost pppd[5150]: Using interface ppp0
Mar 24 10:16:08 localhost pppd[5150]: Connect: ppp0 <--> /dev/modem
Mar 24 10:16:10 localhost pppd[5150]: Serial line is looped back.
Mar 24 10:16:10 localhost pppd[5150]: Connection terminated.
Mar 24 10:16:11 localhost pppd[5150]: Exit.

**********

after it ends, when i click activate again, nothing happens.
and also in windows my modem is on com3 and i believe its ttyS2 in ubuntu. i tried to use that in modem port and the same, it dials but wont connect.

im on:

puresoft pci v.92 fax/modem
using the linuxant modem.

btw, what does this mean.

"serial line is looped back" mean?
Device ttys@ is locked by pid 3860

these are some of the entries i found in logs. (minor)

---

### Post by pugrit on 2005-03-26
any suggestions?

---

### Post by jazzer on 2005-03-26
Have you tried running `sudo pppconfig`?  That will configure the pon command. Going by the log under for 'Computer' -> 'System Configuration' -> 'Networking', I would suggest you're not getting authenticated.  Under the OUTBOUND sections of your /etc/ppp/pap-secrets file add:

your_username    *    "your_password"

Also, make sure under your /etc/ppp/options file that +pap is uncommented.  That's my suggestions.

---

### Post by pugrit on 2005-03-27
i already tried pppconfig and nothing works in pon. but i havent tried the pap-secrets though. il try that one asap.

now i cant dial. it used to dial and i coudl hear the modem dial but now it only says serial connection loped back...no sounds at all.

mayb ei need to recongure everything again including my winmodem.

anyways..thanks

---

### Post by smarttaz on 2005-03-27
1. Check with 'ls -l /dev/modem' if it really links to /dev/ttyS2 (for a COM3 modem).
If not, issue a 'sudo ln -s /dev/ttyS2 /dev/modem'.
Please note that if your modem is not recognized at boot time, you may get this link deleted and/or 'loopbacked' again during the next reboot.

2. For using 'sudo wvdial', first 'sudo wvdialconf /etc/wvdial.conf'.
After running it, 'sudo nano /etc/wvdial.conf' for setting at the end of this cfg file:
Phone =
Username =
Password =

Goof luck!

---

