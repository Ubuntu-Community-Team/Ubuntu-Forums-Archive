---
title: "network-manager and vpnc permission problem?"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by syutzy on 2006-08-31
I have network-manager, vpnc, and network-manager-vpnc (from linux2go.dk) installed, and seem to be having a problem connecting to my VPN.  I've had this setup working before, but can't seem to remember how I did it.

When I try to connect to my VPN, network-manager-vpnc reports that it's connected, but really it isn't.  That is, my connection goes dead.  Trying to connect using vpnc in the terminal gives a "permission denied: cannot open port 500", but including a sudo beforehand makes the connection work beautifully.  I'm thinking that if network-manager was running with sudo permissions, it would be successful.

So my question is this: how can I change the way network-manager is started when I log on (to use sudo/gksudo)?

---

### Post by PhrankDaChickenGeek on 2006-10-30
I'm having the same problem. Anyone?

---

