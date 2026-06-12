---
title: "Can't disable ipv6"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by jgibson on 2008-08-25
I've aliased net-pf-10 off and blacklisted ipv6, but I've still got ipv6 running. Any ideas?

---

### Post by jpkotta on 2008-08-26
ipv6 can't be unloaded once loaded.  You have to restart to get rid of it.

---

### Post by jgibson on 2008-08-26
I have rebooted, several times.[HTML][/HTML]

---

### Post by dmizer on 2008-08-26
More informaion here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Do you have a service which is requesting ipv6?

> NOTE: Blacklisting a module does NOT prevent a module from being loaded if it is needed by a system service, regardless of the fact that it has been blacklisted. Besides, it does NOT prevent the module from being modprobe'd by root.

---

### Post by jgibson on 2008-08-26
Thank you, this was helpful.

---

