---
title: "ssh problem - will not connect right after boot"
date: 2017-10-17
forum: Networking &amp; Wireless
---

### Post by norviller on 2017-10-17
I'm having issues with making ssh connections.  Right after the server is rebooted I get public key errors connecting to that server.  If I move a keyboard+monitor and login in directly then remote ssh sessions connect successfully.  It only takes one time directly, logout immediately afterwards, and then everything works fine...until the next reboot.

Any ideas?

---

### Post by TheFu on 2017-10-19
Look at the client and server log files.  All the answers are in there. May need to turn up the "verbose levels" to see more. I'm talking about the ssh stuff.

It could be as simple as the hostname and IP (DNS) not matching.  The logs will clarify.

On Unix systems for any errors, **always** check the log files first.  Always.

---

