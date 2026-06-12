---
title: "Localhost is not working without internet connection"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by dpacmittal on 2010-04-17
I've recently noticed that my localhost stops working when internet connection is disconnected. I use pon and poff to connect and disconnect my internet.

When I ping 127.0.0.1 or localhost, it is successful. However, [http://localhost/](http://localhost/) and [http://127.0.0.1/](http://127.0.0.1/) gives a Could not reach server error. I've tried restarting the apache and checked its config files for any errors.

I've also checked my /etc/hosts file but it is fine.

I don't know in which direction I should go further to resolve this issue. Any help would be appreciated.

EDIT: Apache/2.2.12 (Ubuntu)
Ubuntu 9.10 Karmic
Kernel: 2.6.31-20-generic

---

### Post by gmargo on 2010-04-17
Is apache really listening on localhost port 80?  Test with "telnet localhost 80" and "sudo lsof -i :80".

Could also be a routing table issue.  "netstat -rn" to dump the routing table.

---

### Post by dpacmittal on 2010-04-17
Okay, just after trying another browser, I found that it works on Firefox and Opera. This is a problem just with chrome.

Thanks for help.

---

### Post by dpacmittal on 2010-04-17
Found an issue reported about the same here:
[http://code.google.com/p/chromium/issues/detail?id=8910](http://code.google.com/p/chromium/issues/detail?id=8910)

---

