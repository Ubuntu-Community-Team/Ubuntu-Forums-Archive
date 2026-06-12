---
title: "Terminal Server Client Issues Connecting to Server 2003R2"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by -cman- on 2008-03-16
I got disgusted with Vista and finally did what I've been threatening to do for about 6 months, installed Ubuntu  7.10.  But in order to keep this OS and work in it I need connectivity to my workplace terminal server for access to Outlook/Exchange and legacy Office 2007 files.  

Using the Terminal Server Client in RDP 5 mode, I plug in username, password, AD domain name.  The connection is made but the result is either a blank remote desktop login screen (grey background) or a half-drawn login screen (see screenshot).  After awhile the error is, "connection reset by peer".  I get the same result doing ```
rdesktop -g5 90% ipaddress
```.  This happens whether I use the tsclient app and select the en-us keyboard or let autoselect do its thing. 

Also, and this is the fun part: I get the same result running XPSP2 in VM Workstation 4 on this laptop. Hardware: HP nx9420 laptop.  Broadcom NIC, ATI x1600 display..  1.5GB RAM.

[IMG]http://www.cman.cx/img/TSC_error.png[/IMG]

I have admin rights on the remote server which is a Server 2003 R2 running Terminal Services.  The RDP settings are all pretty generic. RDP v5 is on.

Not sure where to go from here.  The remote server is working fine as I can access it from an XP box here in the house.  I'll monitor this thread to if you have any questions feel free to ask.

---

### Post by -cman- on 2008-03-17
Update:  The connection works with the settings above (default RDP v5) on the office LAN.

---

### Post by dca on 2008-03-17
I'm probably not going to be much help but the times I remote into MS Exchange Server i've always used just 'RDP' not 'RDPv5' from the drop-down in Terminal Server Client.

---

### Post by MountainX on 2008-04-02
> **dca said:**
> I'm probably not going to be much help but the times I remote into MS Exchange Server i've always used just 'RDP' not 'RDPv5' from the drop-down in Terminal Server Client.

RDPv5 is required for common clipboard functions.

---

