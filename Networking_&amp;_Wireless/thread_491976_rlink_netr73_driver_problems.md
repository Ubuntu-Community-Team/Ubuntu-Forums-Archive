---
title: "rlink netr73 driver problems"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by glendavee on 2007-07-04
I've used ndiswrapper to try to install driver for an inbuilt usb wireless card on a new laptop. 
Driver has installed, but can't get it to work, 
output from ndiswrapper -l :
netr73 : driver installed
              device present (18E8:6229) present  (alternate driver : rt73usb)

iwconfig output looks ok :
IEEE  802.11g   ESSID:"abcde"
Mode : Managed   Frequency: 2.462 GHz Access Point :  00:30:F1:E9:DC:70
RTS thr:off    Fragment thr - 2346B
Link Quality:0 Signal level :0 Noise level :0
etc etc

Any ideas or suggestions please

---

### Post by glendavee on 2007-07-05
Problem solved, I think, with a bit of help from other threads. Answer seems to be to blacklist the rf73usb driver in /etc/modprobe.d/blacklist.

---

