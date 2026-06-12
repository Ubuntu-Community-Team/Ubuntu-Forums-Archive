---
title: "ipconfig /flushdns equivalent command?"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by crypticstatic on 2006-09-07
Is there an equivalent command in linux similar to ipconfig /flushdns in Linux? I looked at ifconfig but didnt see a switch that I can use to do that.

Is there another command that can do this?

Thanks in advance!

---

### Post by tbonius on 2006-09-07
Linux doesnt cache DNS like Windows does.  What exactly are you trying to do?  Double check your /etc/hosts and /etc/resolv.conf file to verify DNS settings.

T

---

