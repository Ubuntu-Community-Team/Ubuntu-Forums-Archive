---
title: "Network Printing with CUPS"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Mickeysofine1972 on 2007-08-13
Hi

I have managed to detect my network printer which on my works network. I have successfully installed the drivers and it seems to have no problems configuring.

I have only one problem, how do I supply cups with a username and password to use when it sends jobs to the printer? the username and password are not the same ones I use to login to my ubuntu box either.

anyone know how this is done?

Mike

PS:

I get this error in my cups /var/log/cups/error_log:

E [13/Aug/2007:12:41:23 +0100] cupsdStartBrowsing: Unable to bind broadcast socket - Permission denied.

---

### Post by 1/0 on 2007-08-13
Do you really want a password or are you having a problem without one? Cups doesn't need one, instead you can restrict the ip:s in /etc/cups/cupsd.conf

I think you can add a user in the config file or by:

```
# lppasswd -u allow:user
```

In XFCE there is a print configuration under settings where you can add users.

---

### Post by Mickeysofine1972 on 2007-08-13
the username and password are needed because its a restricted printer. so I need to login to the printer to authenticate

Mike

---

