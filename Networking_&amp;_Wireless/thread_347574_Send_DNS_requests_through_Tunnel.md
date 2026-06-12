---
title: "Send DNS requests through Tunnel"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by jrbush82 on 2007-01-27
I've setup an SSH tunnel to bypass limitations placed on me at work.  However, the main limitation is a DNS hole that they have.  It resolves addresses like mail.google.com to 127.0.0.1.  I can't edit my hosts file because I don't have administrator rights.  The tunnel works, but DNS requests are still sent to the local DNS servers, and they don't allow UDP/TCP 53 outbound except from the Internal DNS servers.

The question:  Does anybody know how I can tunnel DNS requests as well as web traffic?  I'm limited to using IE6.

---

