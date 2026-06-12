---
title: "Unable to get TOR up and running"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by pieroxy on 2008-06-26
Here is what I did:

```
sudo aptitude install tor
```

Then I added the line "forward-socks4a / localhost:9050 ." in the /etc/privoxy/config file.

Every time I try to connect to tor, either through the "TorButton" firefox extension or the "torify" command, I see the following in the /var/log/tor/log:

```
Jun 24 15:51:10.441 [notice] Tor 0.1.2.19 opening log file.
Jun 24 15:51:10.740 [notice] I learned some more directory information, but not enough to build a circuit.
Jun 24 15:59:48.754 [notice] Application request when we're believed to be offline. Optimistically trying directory fetches again.
Jun 24 16:01:48.522 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)

```

Does anyone has an idea? 

Am I in the correct forum section ?

---

### Post by pieroxy on 2008-06-26
Bump... Am I in the correct forum over here ? I am not so sure now....

---

