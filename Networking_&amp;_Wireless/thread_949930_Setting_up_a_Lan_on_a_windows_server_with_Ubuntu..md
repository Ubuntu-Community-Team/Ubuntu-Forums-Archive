---
title: "Setting up a Lan on a windows server with Ubuntu."
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by morissette on 2008-10-16
How do I recognize my pc from my Windows server?

---

### Post by cariboo on 2008-10-16
Install samba

a short answer for a short question.

Jim

---

### Post by morissette on 2008-10-16
Samba is already installed and ive messed with a bit but I still cant find my computer from my windows pc. Although I connect to the router and the router picks up my IP.

---

### Post by Iowan on 2008-10-16
> **morissette said:**
> Samba is already installed and ive messed with a bit but I still cant find my computer from my windows pc. Although I connect to the router and the router picks up my IP.Is Samba-server installed? Samba client comes pre-installed, so viewing Windows shares from an Ubuntu box *shouldn't* be difficult, but the server must be installed when you want to share *from* the Ubuntu box.  Some threads suggest SMBFS must also be installed.  Another common problem is not having anything shared - although the machine at least shows up...

---

