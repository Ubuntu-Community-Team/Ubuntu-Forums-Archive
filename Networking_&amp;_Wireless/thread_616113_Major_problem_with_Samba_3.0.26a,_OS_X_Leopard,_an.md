---
title: "Major problem with Samba 3.0.26a, OS X Leopard, and symlinks!"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by mrogers on 2007-11-17
Today I upgraded my home file server to 7.10. Immediately I began to experience problems when browsing Samba shares containing symlinks on computers running OS X 10.5 Leopard. The links are not able to be followed; Finder reports them as dead aliases. It's as if the "follow symlinks" option in smb.conf is turned off, even though it's on by default (and I put it in there anyway just to be sure).

My Apple TV (which runs OS X 10.4) and Windows XP machines have no problems browsing these shares, so it is definitely isolated to Leopard (both 10.5.0 and the recent 10.5.1 update experiences the problem). I [found a discussion]("http://discussions.apple.com/thread.jspa?messageID=5808232") on Apple's support pages indicating someone else has had a similar problem with the same version of Samba currently in Ubuntu 7.10 (which is 3.0.26a-1ubuntu2.2). Unfortunately, it looks like the solution is to downgrade to an earlier version of Samba, so it appears the fault lies with that.

So my question is twofold: clearly this is a major bug, and I'm curious if anyone on here has run into it and how soon we can expect a fix. Second, I've never downgraded anything on my Ubuntu box before...how do I do it?

---

### Post by mrogers on 2007-11-17
Naturally, as soon as I make a post I find something that fixes my problem. I added "unix extensions = no" to my smb.conf file; that makes Samba behave like older versions.

More discussion of the matter [here]("http://forums.macosxhints.com/showthread.php?p=423988").

---

