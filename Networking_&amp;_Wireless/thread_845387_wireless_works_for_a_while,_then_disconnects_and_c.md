---
title: "wireless works for a while, then disconnects and can't recover"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by froody on 2008-06-30
I'm setting up Ubuntu on a family's machine. Everything looks great, except the wireless connection. I boot up, log in, and the NetworkManager applet lets me pick the right network. Everything looks great. But after a while (sometimes a minute, sometimes an hour, ...) the connection is lost and then never recovered. Logging out and back in again doesn't help. The only thing that seems to fix it is rebooting ubuntu.

I've attached a syslog of when that happens. Does anybody have any ideas on how to fix this? I'm replacing a spyware-ridden Windows setup used for web browsing with this one, and I want Ubuntu to look good.

Tim

---

### Post by froody on 2008-06-30
I just installed the latest Netgear drivers through ndiswrapper (using ndisgtk, very easy). That seems to have fixed the problem. It's pretty confusing that it mostly worked before then, though.

Tim

---

