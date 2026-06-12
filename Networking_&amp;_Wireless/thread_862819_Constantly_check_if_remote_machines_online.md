---
title: "Constantly check if remote machines online?"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by MobiusNZ on 2008-07-17
Hi guys,

I'm not too sure how to phrase this succinctly so google isn't helping me much. I'm after a program (probably running as a daemon) that constantly pings (or something similar) remote machines to make sure that they are still alive. I want that program to email me as soon as a machine is noticed to be down.

Is there a package that does this? If not, how would I go about scripting this? I don't think cron will let me do it any more than once per min, and I want it to check every few seconds..

---

### Post by mdcatc on 2008-07-18
You'll want to google NATS (Network Automated Testing System) or "network monitor",  FreeNats is pretty good and most of them have notification services both email and SMS text to your phone.
If you have a windows box on your network you could load [www.spiceworks.com](www.spiceworks.com) which runs on windows, but can scan all os types and gives you a bunch of additional information and alerts like low disk space etc.

LunarDraco

---

