---
title: "Netstat Interpretation - Ubuntu 7.04"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by nixscripter on 2008-04-12
That's a lot of output. You weren't kidding when you said server.

I can't tell who the person in question is. What is IP is he logged in from? The **last** command should be able to tell. With that, run netstat again, preferably filtering through grep first, and maybe I can tell you something.

As for what he might be doing, two things come to mind right away: he could be running with shell history turned off, or he could be using ssh for a non-login function, like tunneling or running a specific command. Non-login shells (and some non-bash shells like dash) will not record history.

---

### Post by nik.martin on 2008-04-15
99.95% He's running a bittorrent node.  That's what netstat looks like when a bittorrent client is running.

---

