---
title: "which config is transmission daemon using"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-22
Dear Forum,

I've installed transmission daemon but can't get the web interface to work after reinstalling Ubuntu.

I notice that there are a number of configurations files
/home/user/.config/transmission-daemon (for each user)
/var/lib/transmission-daemon

How do I know which user started the daemon? How can I ensure that the daemon is started by the user I assign?

TIA


Richard

---

### Post by fluxbuntu on 2009-11-22
Once you've run the daemon, running top should show you what user is running the process.

---

