---
title: "[SOLVED] poptop reconnect problem"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by rivalarrival on 2008-01-18
I've got a minor problem with poptop. I've got windows clients connecting to a poptop server running on gutsy. The first time they connect, no problem. However, after disconnecting, the client can no longer reconnect until I restart pptpd.

Fortunately, the pptp connection is pretty stable, and this isn't causing major problems.

Any thoughts?

---

### Post by rivalarrival on 2008-01-19
Well, as solved as it can be.  Linksys took a big step backwards, disabling incoming pptp connections on the RT31P2. They left the user interface about VPN passthrough intact, but didn't bother to actually forward the GRE protocol through the router.

It's frustrating, because I can get it to work once, and I assumed it was the server because restarting it would allow it to work properly again.

Writing to Linksys, let's see if they'll do anything to fix it.

---

