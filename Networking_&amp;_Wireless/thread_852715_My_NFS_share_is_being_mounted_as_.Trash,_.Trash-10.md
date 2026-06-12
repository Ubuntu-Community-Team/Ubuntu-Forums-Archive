---
title: "My NFS share is being mounted as .Trash, .Trash-1000, and .hidden"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by edmccaffrey on 2008-07-07
Hello,

I have an NFS share set to be mounted to /home/[username]/dev.  At first everything was working fine, but now that folder is always empty and I see the three items mentioned in the title as drives, each with the full contents of my share.

My /etc/auto.master contains:
/home/ed/dev	/etc/auto.dev

And my /etc/auto.dev contains:
*	192.168.1.100:/development

I assume that it is some effect of logical deletion; does it think that the entire share is trash?  How do I get it to work correctly?


Thanks.

---

### Post by edmccaffrey on 2008-07-08
Has anyone else experienced this behavior?

---

