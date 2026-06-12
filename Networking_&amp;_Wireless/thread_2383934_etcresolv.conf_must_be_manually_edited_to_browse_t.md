---
title: "/etc/resolv.conf must be manually edited to browse the Internet"
date: 2018-01-31
forum: Networking &amp; Wireless
---

### Post by seanmalone314159 on 2018-01-31
Hi everybody,

Unless I manually add nameservers to my /etc/resolv.conf this file will not update.  I can't connect wireless with no problems but /etc/resolv.conf doesn't update.  Anybody experience this?

Sean

---

### Post by linuchsan on 2018-01-31
Edit **/etc/dhcp/dhclient.conf**
Uncomment **prepend domain-name-servers 127.0.0.1**
Replace **127.0.0.1** with your isp dns, or use 8.8.8.8

---

