---
title: "Should I install drivers for D-Link DPR-1260 Print Server?"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by dlmoak on 2008-05-31
I'm running 64-bit Ubuntu.  

1. The D-Link printer server sees my printer and connects to my wireless access point.
2. My USB wireless network adapter connects to my wireless access point.
3. I setup my printer on System>Administration>Printing using the following settings:
Host: DPR1260
Queue: Stylus88
which created this device url:
lpd://DPR1260/Stylus88

I am not able to print.  I installed no drivers for the print server. Should I? and, if so, how do I go about it?  If not, any suggestions as to what I should do next?  The USB adapter is an Ativa Wireless G and the WAP is a Linksys WRT54G ver. 2. The Windows driver for the D-Link is named odwgu.sys.

Thanks.

---

### Post by dlmoak on 2008-06-01
I installed gnome-cups-manager and changed the port from LDP to tcp/ip connection and test page prionted perfectly.

---

### Post by johnmac1952 on 2008-09-19
Using 8.04 and installed the gnome-cups-manager also and finally got DLink DPR1260 to work also changing it like above. This is on a 32bit system. Thanks for the info that finally got me some satisfaction !!!!


:popcorn:

---

