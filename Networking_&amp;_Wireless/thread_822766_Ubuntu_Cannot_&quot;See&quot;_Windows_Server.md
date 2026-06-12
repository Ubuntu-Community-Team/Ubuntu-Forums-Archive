---
title: "Ubuntu Cannot &quot;See&quot; Windows Server"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Heeter on 2008-06-08
Hi All,

My new Ubuntu setup cannot "see" my Windows 2003 file server. It does list the other Windows machines in the network, but not the actual file server.

The file server does not have it's firewall on, it is disabled.

What steps can I take to resolve this?

Thanks

Heeter

---

### Post by superprash2003 on 2008-06-08
are you able to ping the windows server from ubuntu?

---

### Post by askreet on 2008-06-08
Windows Server 2003?  You may have NetBIOS broadcasting disabled.  I believe that's where Ubuntu gets it's network browsing information.

---

