---
title: "Timeout waiting for PADS packets"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by SlowRedFox on 2008-02-27
I've been setting up an old box as a server/router, and all was going well until I hit the apparently rather common PPPoE connection error:

> 
Timeout waiting for PADS packets
Unable to complete PPPoE Discovery


I've searched both the forums and the net but have come up with nothing of use.

Occaisonally, repeating 
```

poff dsl-provider
pon dsl-provider

```
will result in a successful connection. Sometimes this connection will last for quite a while; other times only minutes. I've tried this both with and without sudo, but to no avail.

The modem/router I'm using in this setup appears to be rather flaky when not in bridge mode, not allowing PPPoE connections at all, although PPPoA will connect successfully, even tho PPPoE has worked in the past. Could this be the cause of the error? Or is it a dodgy phone line or something of that sort? I'm at a loss here - networking is not my forte.

---

### Post by SlowRedFox on 2008-02-27
After an extended period between attempts, PPPoE connected successfully. I don't know if this is a clue to the the cause: I saw a post somewhere that suggested this could be a faulty line?

---

