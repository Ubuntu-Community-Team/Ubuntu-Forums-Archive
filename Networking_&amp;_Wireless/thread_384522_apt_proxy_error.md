---
title: "apt proxy error"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by diogosousa on 2007-03-14
Hi,

Recently I tried to use apt-get behind a proxy without success. 

But when i got home (no longer behind a proxy) i keep getting "zion couldn't be resolved" (zion is the proxy server at work). I've checked if there is any proxy set but there is none. Where else can i look for the proxy settings?

Thanks in advance and excuse my english.

---

### Post by Dr. Nick on 2007-03-15
System - Preferences - Network Proxy maybe?

---

### Post by clov on 2007-03-15
> **diogosousa said:**
> Hi,

Recently I tried to use apt-get behind a proxy without success. 

But when i got home (no longer behind a proxy) i keep getting "zion couldn't be resolved" (zion is the proxy server at work). I've checked if there is any proxy set but there is none. Where else can i look for the proxy settings?

Thanks in advance and excuse my english.

to  use apt behind a proxy you need to configure  /etc/apt/apt.conf  (replace "false" with your proxy)

---

