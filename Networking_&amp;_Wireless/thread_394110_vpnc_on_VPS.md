---
title: "vpnc on VPS"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by earonne on 2007-03-26
Hi,

I'm trying to establish a VPN connection using vpnc. I try this:

```
vpnc-connect --enable-1des
```

and the result is:

```
RTNETLINK answers: File exists
vpnc-connect: socket(SOCK_RAW) failed: Address family not supported by protocol

```

I'm using Edgy, kernel 2.6.9 on a VPS. Any ideas why i'm getting this error???

Thanks!!!!!

---

### Post by earonne on 2007-04-07
After some research, the problem seems to be no support for IPSEC ESP. In my case, this option CONFIG_INET_ESP is not enabled in the kernel.

---

