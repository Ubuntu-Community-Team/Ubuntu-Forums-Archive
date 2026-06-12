---
title: "[SOLVED] PASV FTP via ADSL Router"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by mafitzpatrick on 2007-12-11
Since installing I've never been able to access PASV FTP servers from Kubuntu. I am connecting through an ADSL router (Speedtouch) via ethernet and connections to non-PASV FTP sites work fine.

This hasn't been a problem until today when I find myself needing to connect to a host that only allows PASV connections.  Is this problem likely to be in Kubuntu or the router?  Either way is it something that can be fixed in Kubuntu?

Thanks folks

Martin

---

### Post by mafitzpatrick on 2007-12-12
Having checked with a Windows XP laptop (using SmartFTP) it looks as though it isn't a router problem. Connecting over the same network using PASV/Active works fine on the XP laptop, but under Kubuntu PASV goes nowhere.

Any suggestions of where to look for the problem?

---

### Post by mafitzpatrick on 2007-12-12
If you wait long enough you answer your own question: Connecting with gFTP works, connecting with Konqueror works... so I guess its' just Dolphin that's busted.

Oh well.

---

