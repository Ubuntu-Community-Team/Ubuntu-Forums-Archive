---
title: "TCP problem"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by nise8181 on 2007-10-28
I seem to have a strange TCP/UDP problem while using my wireless connection:

```
ping google.com
``` works, so there is no DNS problem
```
host google.com
``` works as well
```
route -L
``` tells my that I am using eth1 which is my Broadcom43xx WLAN card
As well I am able to establish wireless connection with other mashines and of course there is no mac-filter activated.

but: any protokoll like FTP, SSH, HTTP which is based on TCP doesn't work.

I have disabled ipv6 without any positive result.

OS: ubuntu 7.10 (fresh installation)

Has Ubuntu a desktop firewall which I have to disable?
If not, what could be the reason for that behavier?

Any suggestions are welcome.

---

