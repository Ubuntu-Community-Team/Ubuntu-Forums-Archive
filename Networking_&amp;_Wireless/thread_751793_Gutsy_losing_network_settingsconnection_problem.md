---
title: "Gutsy losing network settings/connection problem"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by the lush on 2008-04-10
Hi, this is a little on the strange side. I have been running 7.10 since it came out and have had absolutely no problems after I did a clean install. Unfortunately the last week or so an issue has developed:

At home I use a PPPOE connection which used to be flawless, now I find that everytime I want to connect I have to re-run pppoeconf, all settings seem to be lost when I shutdown. This never used to happen, in the past I would plug in the cable, boot the system, and it would connect all by its self.

At work and in the bar I use a wireless connection. Again, I had entered the passwords for the connections, and it would automatically connect whenever I was in the office or bar. Now it claims to have connected, but when I open Firefox or Evolution I am told that there is a network connection error. Soon after this it prompts me for the network key, which I give it. The connection bars drop to zero, then reappear but there is still no connection. 

Windows on the same machine shows no problems.

I assume that some settings file or whatever has been messed up, perhaps there has been an update, I really have no idea, but desperately want to fix this. Any help will be greatly appreciated.

---

### Post by dstew on 2008-04-11
This is probably a software bug. A similar bug was reported in Feisty. See [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/rp-pppoe/+bug/97451").  Apparently if you do **poff** followed by **pon dsl-service** it gets going again but people should not have to do this. It would help if you made this a [bug report]("https://launchpad.net/ubuntu/+filebug"). Maybe it will be fixed by Hardy, but I don't know.

---

