---
title: "Vmware Guest to Host networking SLOWWW"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by dguido on 2006-11-14
I have a Windows VM Guest running on VMWare Server.  I've always used WinSCP to SSH to my host OS (Edgy) and grab files when I needed them.  However, lately WinSCP has only been able to muster up about 3k/sec in transfer speeds instead of the usual 5-6 megs/sec.  Why would this happen?  Does anyone have any ideas?

---

### Post by dguido on 2006-11-22
bump, still having this problem.

---

### Post by dguido on 2006-11-22
ethtool -K eth0 tx off

that fixes the problem.

---

