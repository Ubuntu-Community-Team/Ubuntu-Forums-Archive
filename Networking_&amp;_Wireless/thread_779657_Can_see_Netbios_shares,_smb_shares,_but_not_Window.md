---
title: "Can see Netbios shares, smb shares, but not Windows shares"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by bmowder on 2008-05-02
All-

  This is an an odd one-  I have Ubuntu 8.04 - the Hardy Heron running on a Toshiba Tecra 8200.  It is a member of an AD domain we'll call 'wazoo.com', with a short name alias (netbios) of 'CorpNet'.

  I have configured it using likewise and SADMS, and I can mount any shared file system via 'connect to server'.  The weird thing is, when I browse the network via Nautilus, If I open any server on the network, one of three things happens:

  If it's a Unix machine with a samba server, I can see the shared folders as icons.

  If it's an NT 4.0 machine with netbios/wins shares, I can see the shared folders as icons.

  If it's a windows XP or Windows 2003 server with AD shares, I can't see the folders in the Nautilus browser.

  Has anyone else seen this?  What gives?

Thank you for reading this,
Barney

---

