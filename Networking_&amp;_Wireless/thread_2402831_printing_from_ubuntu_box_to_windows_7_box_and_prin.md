---
title: "printing from ubuntu box to windows 7 box and printer"
date: 2018-10-04
forum: Networking &amp; Wireless
---

### Post by mark allyn on 2018-10-04
Hello,

I have a small wireless LAN.  On one node I have a Ubuntu 16.04 box (32 bit).  I have a printer connected to a Win 7 32 bit box.  How do I set about sharing the printer between these two systems.

Any help would be greatly appreciated.

Mark Allyn

---

### Post by TheFu on 2018-10-06
Ive always gone the other way - printer connected to Linux, Linux running print server (CUPS) then have the Windows machines use IPP to print.  The details depend on the exact printer model.

---

### Post by mark allyn on 2018-10-06
Hi TheFu,

I'd do it the way you suggest, but the printer associated with my Ubuntu machine is no longer usable.  I thought from stuff I was reading that somehow SAMBA could do the necessary interfacing between Linux and Win 7, but I haven't been able to find out how SAMBA works.  

My Ubuntu box can "see" the Win 7 host, That is, I can ping the Win 7 machine with my Ubuntu box, and it shows up on the system settings for printing as present on the network.  But, nothing happens when I try to print.

Regards,
Mark

---

### Post by TheFu on 2018-10-06
Win7 would need to run a network print server.  I have no idea if that is possible or not. You can google for that answer just as well as I can.  IPP or LPR are the normal printer protocols used.

Samba can be used as part of running a print server on Linux. Could it be that is what you are seeing?

When 2 different computes communicate, there is a protocol that is specific to the way they are supposed to talk.  For printing there are a few acceptable protocols, none *magically* work.  Something must be setup and configured on both the server and the client side.

---

