---
title: "Tor has stopped working"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by berencamlost on 2008-09-29
I had Tor installed and working for a day. Yesterday i turned on Torbutton in Firefox and tried to check a website but received an error message that privoxy had a forwarding failure. I've checked around and the problem seems to by that Tor isn't starting, when i try to restart it i get this...

```
 sudo /etc/init.d/tor start
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
ABORTED: Tor configuration invalid:
Sep 29 10:23:24.447 [notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
Sep 29 10:23:24.447 [warn] Failed to parse/validate config: Unknown option 'forward-socks4a'.  Failing.
Sep 29 10:23:24.447 [err] Reading config failed--see warnings above.
```

apparently tor has decided that "forward-socks4a / localhost:9050 ." is an unknown option. Just wondering why Tor would stop working after it was working fine (albeit briefly) and how i can fix it.

---

