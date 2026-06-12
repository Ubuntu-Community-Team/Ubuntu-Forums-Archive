---
title: "Trouble with DNS server"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by tfkaehler on 2010-04-02
Stupid problem.  We just moved offices and lost our IT guy, at the old office our server worked fine.  Plugged it in at the new office and it doesn't work anymore.  How do I fix this?  I assume its some problem with having a new IP address and the DNS not mapping correctly.  Also, I tried adding the new IP address to the file /etc/resolv.conf but that didn't seem to change anything
Thanks for helping a nube

---

### Post by llamabr on 2010-04-02
I'm afraid we'll need much more information than simply 'my internet doesn't work'.

Why do you assume it's a dns problem?  What dns servers are you using?  before you go messing up your /etc/resolv.conf, tell us what's in there, by copy/paste.

Are you using a router?  How many boxes?  Are they connecting via wireless?  What OS are they running?  Can you ping the router, or the world?

Did you burn the bridge with your old it guy?

---

### Post by Iowan on 2010-04-02
> **tfkaehler said:**
> Stupid problem.  We just moved offices and lost our IT guy... Did you check in the box with the install CD's 8-[
(Sorry - feeble attempt at humor)
Same ISP (ie. same IP address?) or does it not work locally either? Does it  HAVE an IP address (**ifconfig -a)** Can it ping anything? Cabling all properly connected (e.g. WAN cable doesn't plug back into LAN port)?

---

