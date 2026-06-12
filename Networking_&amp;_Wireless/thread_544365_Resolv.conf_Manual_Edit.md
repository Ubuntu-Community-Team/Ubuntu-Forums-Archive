---
title: "Resolv.conf Manual Edit"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Senathon on 2007-09-06
Does anyone knows how I can set /etc/resolv.conf with manual editing?  I am using a static IP and do not want any other application to overwrite the file.

Robert

---

### Post by stalker145 on 2007-09-06
> **Senathon said:**
> Does anyone knows how I can set /etc/resolv.conf with manual editing?  I am using a static IP and do not want any other application to overwrite the file.

Robert

Have you tried using "System ~> Administration ~> Network" to set your static IP, DNS, etc? That's how I do the four computers on my home network and I haven't had any applications overwrite them yet... yet ;)

---

### Post by noob12 on 2007-09-06
If you have only statically configured interfaces, make sure that the setup of all of your actual interfaces is specified in **/etc/network/interfaces** (either by direct editing, or via the System | Administration | Network gui).  If you have any DHCP interfaces or "roaming interfaces" (interfaces on your box that are not mentioned in your /etc/network/interfaces file), you could get interfering writes to /etc/resolv.conf from NM/dhclient.

---

