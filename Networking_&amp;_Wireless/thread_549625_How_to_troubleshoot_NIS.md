---
title: "How to troubleshoot NIS?"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by tvreeland on 2007-09-12
I've posted questions elsewhere and nobody seems to have an answer, so I'm hoping somebody can help me find my own answers...

A co-worker and I have been trying to set up Ubuntu (7.04) workstations in an environment that is Win2k workstations with FreeBSD servers.

We are having variable success with NIS for authentication.  I HAD a Feisty workstation authenticating (after MUCH hair pulling) and then they put a new server in to replace the old one.  Now I can't get authentication to work.

However, my co-worker has gotten one Feisty Workstation to authenticate properly when in single-user mode.  However, he can't log in through the GDM graphical log-in screen.

I'm wondering if there are logs that can let me see more clearly WHY the NIS is failing?  YPCAT PASSWD and all the other stuff checks out fine.  I'm getting what I need from the server to start the whole process.  So, to debug the problem I need a closer look at what's happening DURING the log in.  And, no, I can't go looking at the server's logs.  I need to work off of the client's info, unfortunately.

I'm also wondering if this is a Feisty problem?  I've seen lots of similar posts!  Did earlier versions have trouble with NIS?

If you can help, THANKS!

---

