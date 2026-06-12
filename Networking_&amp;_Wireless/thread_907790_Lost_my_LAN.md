---
title: "Lost my LAN"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by rerushg on 2008-09-01
Running Hardy (Ultimate Editon) on 3 machines. Folder sharing has been a no-brainer for weeks via our Linksys router. One machine is hard wired eth0 and the other two are wireless. Internet connection for all boxes remains fine.
About an hour ago I rebooted my machine after killing K3B with a DVD burn problem. Then we had no LAN at all. No box can contact any other.

Any ideas please?
Thanks.

---

### Post by cariboo on 2008-09-01
Check the ip addresses on all computers to make sure there are no conflicts.

Jim

---

### Post by rerushg on 2008-09-02
Thanks for the reply, Jim. Iptables looked okay to me and Samba seemed to be running normally. Don't really know what was going on but second reboot of all machines cleared it up. We're back to normal now.
I don't usually post this kind of problem, preferring to dog it down myself but this was a particularly exasperating day of backing up and archiving one machine to prepare for a new OS. Should have been an easy 5-6 hours of just watching tennis and golf on TV while moving files and burning DVD's.
The problems seem to have been rooted in a 2.2G ".mkv" (Matroska Multimedia Container file) that was not a happy camper. I had trouble with the transfer, "CD/DVD Creator" wouldn't handle it, and K3B locked up after allegedly successfully writing it to DVD. Of course, the resulting DVD wouldn't mount.
Don't know what all that's about, especially since I was only handling it as raw data. Perhaps its the size, perhaps it has some control or ID bytes that certain software doesn't like, or maybe it had a surprize inside.:) It all seems to be over now.

Thanks again for the feedback. I'll let you guys know if bugs propagate and start crawling out of my boxes.

Rick

---

