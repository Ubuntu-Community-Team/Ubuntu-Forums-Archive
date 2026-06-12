---
title: "Unable to use wireless adapter"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by mikesena on 2006-11-25
Hi,

I installed Ubuntu 6.06 on my compaq presario laptop.  After having a few initial problems, I logged in and managed to setup wired internet.  Ubuntu detected that I had a wireless device and set it to eth1.  However, I cannot properly activate it and i cannot use it.  I open the networking window, click Wireless Connection and then activate it, it says it is activated but in fact is isn't (when i reopen networking it is back to saying disabled).  I upgraded to 6.10 using the system updater, but that hasn't helped either.  MY laptop has a button on one side that activations the wireless service, but pushing this does nothing.  I cannot find any wireless tools / drivers etc to use in linux that will enable me to activate / deactivate wireless using this button.  I suspect that it isn't enabled, and that is what is preventing me wrong using wireless services.

Does anyone have any suggestions?  I need to have wireless, as wired is only a temporary solution.

---

### Post by ReaderRat on 2006-11-25
See if anything [**[color=blue]HERE[/color]**](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless) helps.

---

### Post by mikesena on 2006-11-25
I actually have the device activated now, but i still cannot connect to networks.  in wifi-radar, i can see the available ones but the connection never succeeds.  HEre's the output from the terminal
> 
stephen@stephen:~$ sudo wifi-radar
dhclient3 --version 2>&1
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:56:3f:ae
Sending on   LPF/eth1/00:90:4b:56:3f:ae
Listening on LPF/eth0/00:02:3f:24:13:ae
Sending on   LPF/eth0/00:02:3f:24:13:ae
Sending on   Socket/fallback
Stale pid file.  Removing
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:56:3f:ae
Sending on   LPF/eth1/00:90:4b:56:3f:ae
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9

It does not actually connect.

Help?

---

### Post by spd106 on 2006-11-25
Hi, could you please post the output of **lspci** and **iwconfig**. If it's a Broadcom card then I suggest you try ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

---

