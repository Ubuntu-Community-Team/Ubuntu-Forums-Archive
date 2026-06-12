---
title: "SquidGuard URL rewrite not working"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by The_Pariah1 on 2014-08-26
I am trying to configure a Squidproxy server to append Google Safe Search to search lookups for a education organization.  I managed to get Squid proxy installed easily, but I have been having a hassle trying to implement the url-rewrite in SquidGuard.  I can pass traffic through Squid not problem, but I have struggled to implement a url-rewrite.  I have a simply SquidGuard.conf below, but it doesn't work.


SquidGuard.conf
```
dbhome /usr/local/squidGuard/db
logdir /usr/local/squidGuard/log
rew google {
 s@(.*google\..*/(custom|search|images|groups|news)?.*q=.*)@\1\&safe=active@i
}
acl {
 default {
 pass any
 rewrite google
 }
}
```

Any ideas?

---

### Post by The_Pariah1 on 2014-08-27
Anybody have any ideas?

---

