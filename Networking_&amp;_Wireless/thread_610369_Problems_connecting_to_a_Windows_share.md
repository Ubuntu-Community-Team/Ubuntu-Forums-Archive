---
title: "Problems connecting to a Windows share"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by FLCLFan on 2007-11-11
When i try to go into shared files on any of the Windows computers on my network I get:
> The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Windows Network: dell".
In this case the computers name is dell.

Im trying to access then using Places -> Network.

Does anyone know why i cannot get into these windows shares?

Thank you

---

### Post by Peter09 on 2007-11-12
First, check if you can ping the share machine by IP address, then try by Host name. If you succeed by IP address but not by host name then you have (as I have) a problem with DHCP.

You can mount shares by IP address easily enough but its a problem if you cannot use static IP address, and its clumsy.

---

