---
title: "Closing Intrepid RDP connection produces various errors"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by kevindontenville on 2008-11-05
Hi All

Just moved my main desktop to Intrepid and find that when connecting via RDP/TSCLIENT to Windows machines when I closed the connection I would get errors that produce a countdown to reconnection attempt.

These were:

channel register error - initializing sound-support failed - NOT IMPLEMENTED - system pointer message 0x7f00 - major opcode of failed request 23 (X_GetSelectionOwner) 

when sound to local computer selected or when not selected:

BadAtom - (invalid Atom parameter)

However when I changed from RDPv5 to just RDP protocol all worked fine.  Previously with Hardy to avoid an error on closing I had to ensure the correct keyboard was selected but it worked fine on RDPv5.  These errors happen when connecting to W2K and W2K3 servers full-screen or not.

Anyone else tried this and had similar?

:confused:

---

