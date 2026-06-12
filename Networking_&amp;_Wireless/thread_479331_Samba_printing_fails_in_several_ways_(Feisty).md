---
title: "Samba printing fails in several ways (Feisty)"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by mo-seph on 2007-06-20
Hello,

I've been trying to get my laptop to talk to a printer on my uni network, using smb. If I run 

smbclient <hostname> -L

then I get back the expected list of printers. However, if I enter the URI for the printer in any of gnome-cups-manager, systemsettings/printers, CUPS admin (localhost:631), I cannot get the printer to work.

The two guis (gnome and systemsettings) all attempt to scan for samba shares, but fail to come up with the list of printers returned by smbclient (further, the gnome client starts asking me for a password for every server on the network, which quickly gets boring ;) )

When I input the information by hand, they do an inventive job of mangling the URIs.

When I try to print a test page using gnome or systemsettings, it tells me that the job is printing, and then that it's finished, but nothing ever comes out of the printer; this happens all the time, even if I put in loony values.

Does anyone have any suggestions for things to try? I'm a bit worried that neither GUI client can correctly scan a samba server!

---

### Post by mo-seph on 2007-06-20
Quick followup: I can print fine using smbspool, so it's an issue with cups->samba and/or the cups guis

---

