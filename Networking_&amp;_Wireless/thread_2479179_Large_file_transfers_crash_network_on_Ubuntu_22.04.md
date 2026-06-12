---
title: "Large file transfers crash network on Ubuntu 22.04"
date: 2022-09-17
forum: Networking &amp; Wireless
---

### Post by bertram2 on 2022-09-17
Hi there,

I've encountered a strange problem and hope you guys can help me track it down. This didn't occur on Ubuntu 20.04 LTS, but appeared after I upgraded to 22.04 LTS.

When transferring large files (~ 30 GB) (over a samba share and/or via scp), after a certain amount of time (~ 9 Min. on cable, ~ 18 Min. on wifi) the connection is lost. The ubuntu server can't access any network afterwards, I have to manually restart the network stack (ifdown / ifup). Strange thing is, there are no errors shown in /var/log/syslog, /var/log/samba or dmesg.

Do you have any ideas where else I could search for error messages? Or has anyone encountered similar problems?

Thanks!

---

### Post by TheFu on 2022-09-17
Check the system logs, but as a workaround, use rsync.  rsync will pick up where the transfer failed.  rsync works over ssh by default. No extra options are needed, though I'd guess that rsync must be installed on both sides of the connection.

---

### Post by bertram2 on 2022-09-19
Cheers for the reply. As stated above: dmesg and /var/log/syslog don't report anything...

I've already tried rsync, but it failed as well. However, there I got the hint, that it might have something to do with the compression not functioning properly (as described here: [https://bugs.launchpad.net/ubuntu/+source/rsync/+bug/1971932](https://bugs.launchpad.net/ubuntu/+source/rsync/+bug/1971932))
For rsync, using it without "-z" seems to resolve the problem, but it's still there with scp and samba.

Any other suggestions or hints where I could look at?
Thanks!

---

