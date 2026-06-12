---
title: "Forcing /etc/hosts"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by awacs on 2008-01-29
I'm looking for a function like 'HOSTRESORDER local bind' in /etc/resolv.conf. Didn't see HOSTRESORDER on the resolv.conf man page.  The prob is that DNS is returning a spurious (for me) value, A conflicting (in gutsy gibbon) HOSTS file value is silently ignored. How can I change this behavior?

---

### Post by hahahan on 2008-01-29
Awacs,

I don't realy understand the question but when hosts is ignored, does /etc/host.conf contain the line "order hosts, bind" ? Are you shure the entry in hosts is valid?

Regards.

---

### Post by jetsam on 2008-01-29
Look at /etc/nsswitch.conf and its associated man page.  There's a line in that file labeled 'hosts:', and you want 'files' to be the first entry in that list.  Mine reads:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Yours may have additional stuff in it depending on your set up.  I think you need to restart processes that refer to this file after you make changes-- the man page says it's only referred to once by each process.  The easiest way to be sure you've done this is probably just to restart the computer.

The /etc/host.conf file that hahahan mentioned is probably also worth checking, but there's a comment at the top of mine that essentially says it's deprecated.  Some software may still refer to it, though.

---

### Post by awacs on 2008-01-29
> **hahahan said:**
> Awacs,

I don't realy understand the question but when hosts is ignored, does /etc/host.conf contain the line "order hosts, bind" ? Are you shure the entry in hosts is valid?

Regards.

You did (understand my question) - /etc/host.conf was what I was looking for.

Thanks (I'll try it tonight).

---

