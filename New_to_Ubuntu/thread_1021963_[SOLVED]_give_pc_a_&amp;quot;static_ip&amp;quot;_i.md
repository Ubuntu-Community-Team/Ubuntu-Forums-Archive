---
title: "[SOLVED] give pc a &amp;quot;static ip&amp;quot; in the home network"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-12-26
I have a few machines on my network and I'm wondering how I can make sure each machine keeps the same ip.

After rebooting my desktop sometimes changes from 192.168.1.2 to 192.168.1.3.

This causes problems with ssh.

---

### Post by theozzlives on 2008-12-26
My router acts like a DHCP server in reserving IPs, if yours don't, you can always assign one of your boxes to be DHCP.

---

### Post by billgoldberg on 2008-12-26
> **theozzlives said:**
> My router acts like a DHCP server in reserving IPs, if yours don't, you can always assign one of your boxes to be DHCP.

Yes, my router acts as a dhcp server.

Still, the ip adresses of the computers sometimes change.

---

### Post by theozzlives on 2008-12-26
Go to your LAN settings and reserve your IPs. You'll need the hostname, the IP you want, and  MAC address of each NIC.

---

### Post by billgoldberg on 2008-12-26
> **theozzlives said:**
> Go to your LAN settings and reserve your IPs. You'll need the hostname, the IP you want, and  MAC address of each NIC.

Ok, thanks for the nod in the right direction.

---

