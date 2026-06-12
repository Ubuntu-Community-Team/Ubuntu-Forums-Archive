---
title: "[SOLVED] Active Directory Authentication on log-in"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by jpietari on 2007-08-22
I'm testing out Ubuntu 7.04 in a Virtual Machine (VMWare) at work, which is a Microsoft environment.  I'd like to setup Active Directory authentication on log-in.  As of right now, I can be authenticated by AD, but this happens when I try to connect to a network resource.  I use Password Manager to store my info, but it isn't the best solution.

Does anyone know how to set-up AD authentication at the Login Window?

---

### Post by Wicca on 2007-08-23
Hi,

For that, your Ubuntubox needs to be a member of the AD-domain, same way the Window-clients are.

Have a look at 
[http://sadms.sourceforge.net]("http://sadms.sourceforge.net")

Succes.

---

