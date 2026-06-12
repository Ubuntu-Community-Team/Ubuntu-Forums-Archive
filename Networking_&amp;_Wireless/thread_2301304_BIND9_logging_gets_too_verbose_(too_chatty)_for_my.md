---
title: "BIND9 logging gets too verbose (too chatty) for my taste"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by Grigoriy on 2015-11-01
I've configured logging in my BIND9 server and I have 2 log files: 1) debug.log; 2) query.log. The second one is Okay. No complaints so far. But the first one is too  verbose (too chatty) for me. Like 90% of what it says there I don't even  understand. You get like 100's of thousands of text lines within couple  of hours only. That's crazy! Here how it's set:

```
channel debug_log {
     file "/var/log/named/debug.log";
    severity debug 3;
```

If I understand it right, to make it less verbose (chatty), I can try  debug 2 or simply debug (which defaults to debug 1). Right? The next level (less chatty) would be:

```
severity info; 
```

Right?

---

