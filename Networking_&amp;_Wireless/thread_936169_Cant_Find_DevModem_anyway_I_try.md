---
title: "Cant Find /Dev/Modem anyway I try"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by captain_buckethead on 2008-10-02
hey all
are you familiar with the error
'-->Cannot open /dev/modem: No such file or directory' when setting up wvdial.conf '/etc/wvdial.conf'.
I tried to do what the docs said about using the setserial command, but that didnt work saying that 'Couldn't find package setserial'.
OK, now im confused, because I know that:
1) I have a working modem card (56k) that worked well under Vista.
2) I plugged all the right details into Wvdial.conf, and
3) Also set up a connection with pppconfig.

When I try 'Pon', I get the same message that 'cant find /dev/modem: No such file or directory'.
Is there a step I am missing, and is it possible to find my modem another way?

Glenn.

Running 8.04.1 Hardy Heron 64bit on Amd 2.3 Ghz Phenom.

---

### Post by Paul S on 2008-10-02
Sounds like you need to install a linux driver for your modem.  Some modems do not have linux drivers.  This thread might help:

[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

regards,

---

