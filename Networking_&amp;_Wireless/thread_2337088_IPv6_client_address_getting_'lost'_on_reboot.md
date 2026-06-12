---
title: "IPv6 client address getting 'lost' on reboot"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by xWEkxhW on 2016-09-14
Hi Folks

I am running ISC DHCP6 server on my Ubuntu box. It is issuing IPv6 addresses to clients upon request so that all seems to be working fine. There is one problem I am experiencing with Windows 10 clients. If they are restarted, or if the network interface is cycled down/up, the IPv6 address is lost and the only way to reinstate it is to run the command ipconfig /renew6 which then successfully reinstates the existing IPv6 address.

Does anyone know why this is happening and how to resolve the issue?

Thanks very much!

---

