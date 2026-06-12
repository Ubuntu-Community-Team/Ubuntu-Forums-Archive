---
title: "A per-application firewall?"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by PrinceVince on 2016-09-11
Hello. I finally want to set up a firewall (using ufw) and was wondering if anyone had experience with blocking access on a per-application level, which I used to do in MS Windows and would like to continue. Obviously blocking ports alone cannot achieve this. I read some suggestions on stackexchange about using "cgroups" to either white- or blacklist applications from internet access. I would prefer a whitelisting approach, unless it makes day-to-day internet use cumbersome.

I'd love to hear more about this and assuming this approach is viable, get some help setting it up if I get stuck.

Thanks a lot.

---

### Post by TheFu on 2016-09-11
You can do it through scripting to make it trivial to use, but it isn't trivial to setup.  I think you need a way to run the applications as a different userid and use per-userid firewall rules.  The ideas to use cgroups is a good one and a tool called **firejail** makes it pretty trivial to use/deploy.  Firejail lets you control access to different system capabilities by program - networking is one of those things.

These methods are much more flexible than the Windows method, just takes a little *different thinking* to get a handle on them.  OTOH, Linux isn't Windows, so that is to be expected.  The manpage for firejail was enough for me to get started.  I generally use it to prevent internet-using applications from writing anything to a local file system using the "--private" option, so it doesn't matter what the application does.  You can run a bash shell inside a firejail too and play around some to gain a better understanding of what the different options and settings can do.

Of course, no single tool can provide 100% guarantees.  When it comes to security, a **belt AND suspenders** are best.

---

### Post by PrinceVince on 2016-09-11
**Firejail** looks like the kind of application I'm searching for. Thanks a lot for the suggestion, I'll dive right in!

---

