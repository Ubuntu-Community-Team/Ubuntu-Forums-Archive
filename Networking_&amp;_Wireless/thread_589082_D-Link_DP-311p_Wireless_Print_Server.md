---
title: "D-Link DP-311p Wireless Print Server"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by mechgt on 2007-10-23
So I've got a D-Link wireless print server connected to an HP LaserJet 6P.  When I try to print with it it just comes out as gibberish.  It's setup as a 'TCP Socket, HP JetDirect, RawConnection' type where I just type in the IP Address, and I'm accepting the default port of 9100.

I set it up in Windows using the Standard TCP/IP port and Generic Network Card, and got the same result; gibberish.  When I changed it in WinXP to use the D-Link network card driver, it started working (in XP).... Any ideas?

---

### Post by mechgt on 2007-10-24
Figured it out:

In **System > Administration > Printing**, add a new printer and select your print driver.  This is generic to your printer, and independent of the DP-311 wireless print server.

On the connection tab of your printer properties, select:

**Printer Type:** Network Printer > UNIX Printer (LPD)
**Host:** *IP Address*
**Queue:** Ip1

I've now got a wireless printer that all of my computers can access directly without having a shared printer!  Thanks mechgt!

---

