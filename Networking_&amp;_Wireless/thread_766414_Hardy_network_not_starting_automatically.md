---
title: "Hardy network not starting automatically"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by rrwo on 2008-04-25
I don't use NetworkManager to manager my network. Instead, I have a specially configured /etc/network/interfaces file which works with ifplugd and guessnet to manage my network based on where I am connected with.

This worked fine with Gutsy.  But the networking and ifplugd daemons are not started automatically when I boot or resume form hibernation/suspend, despite them being set up to start in /etc/rc[0-9S].d.

If I manually start the services after logging in, then everything starts up and seems to work fine.

---

