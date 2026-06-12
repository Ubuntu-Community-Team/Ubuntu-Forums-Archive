---
title: "Firestarter blocking Ubuntu Repo?"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by talcite on 2007-03-14
For some reason, Firestarter blocks all my updates from the repos. Is this normal behavior? I have it set on permissive outgoing by default. 

I didn't make any changes to the IPtables manually. 

At the moment, I have to disable IPtables to update. This isn't normal behavior is it? =S How should I work around this? Is the repo IP static?

I also tried adding the repo IP to the allow incoming list. No luck, still have to disable firewall to get a proper update of the repo index =/

---

### Post by bapoumba on 2007-03-14
> **talcite said:**
> For some reason, Firestarter blocks all my updates from the repos. Is this normal behavior? I have it set on permissive outgoing by default. 

I didn't make any changes to the IPtables manually. 

At the moment, I have to disable IPtables to update. This isn't normal behavior is it? =S How should I work around this? Is the repo IP static?
No, this is not normal.
Please check > Preferences > Advanced options > Block traffic from reserved addresses on public interfaces is **unticked** (seen on another thread).

---

### Post by bravemosquito on 2007-03-15
I'd already posted for a problem with them in Launchpad. For unknown reasons iptables 1.3.5, which is my version, are not working very well. Firstly I had exactly the same bug with repositories... After their removal, now I haven't problems in P2P networks, sites now opens every time, Enemy Territory works without lag and online servers are refreshed correctly. Before that the only workaroung is flushin' them on every 10-15 minutes

---

### Post by talcite on 2007-03-16
Ahh... there we go.. it was ticked =P

Thanks =D

---

### Post by bapoumba on 2007-03-16
> **talcite said:**
> Ahh... there we go.. it was ticked =P

Thanks =D
Welcome.

@ bravemosquito: did you remove iptables ???

---

### Post by bravemosquito on 2007-03-16
**bapoumba**, yes. Before the machine there's a pfSense box for routing, I'm calm about intruders

---

