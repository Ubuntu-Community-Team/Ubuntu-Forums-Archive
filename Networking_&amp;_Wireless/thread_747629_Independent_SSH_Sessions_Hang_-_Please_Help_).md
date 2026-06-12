---
title: "Independent SSH Sessions Hang - Please Help :)"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by Nineteen on 2008-04-06
Hey,

We are running OpenSSH_4.7p1 on our Ubuntu, Debian box.
We have multiple SSH Users logged in whom are forwarding traffic via the SSH connection.

What we are finding is random SSH hangs at command line. Eg: One of the sessions suddenly can't type in commands / their forwarded traffic is halted. Then after a moment the commands they tried to type in suddenly show and the forwarded traffic is continued.

This is not a network connection issue because if I personally connect via SSH, tunnel the forwarded traffic... At a random interval it hangs, so I open another SSH connection and can login / input commands etc without any hanging (whilst the previous SSH connection is still hanging).

Any ideas? The main concern is that people's traffic is being halted / stopped for a few seconds every so often.

Please note: The logged in sessions are running a Shell Script that continuously prints a '.' every 10 seconds to keep the connection alive.

Cheers!

---

### Post by Nineteen on 2008-04-06
*bump*

---

