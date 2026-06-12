---
title: "internet"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by afss on 2010-03-21
hello there,i am new to ubuntu n have very less knowledge about using commands..i have a new bsnl wll ct800p phone.ive been trying to connect to internet for the past 3 days but it couldnt help.by surfing google i came to know about wvdial n gnome ppp but it doesnt work eigther..
this is the output for wvdial:
Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check Def Route"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
wat does this mean
can anyone help

---

### Post by dineshs on 2010-03-24
Hope your modem is connected to USB.post the output of
```
lsusb
```
If you have gnome-ppp installed,under setup plese click `detect modem'
What is the result?

---

