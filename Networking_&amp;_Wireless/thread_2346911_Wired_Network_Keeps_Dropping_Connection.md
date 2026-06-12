---
title: "Wired Network Keeps Dropping Connection"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by Westley on 2016-12-19
Hi,

Have a server running 14.04 LTS - Been running like a champ with no problems.

Seems like over the weekend we had some electrical problems at the office. No power for 5+ hours. Long enough for the UPS to drain.

Server booted up this morning with no dirty messages and everything seemed fine.

Problems: Can't stay connected for long to SAMBA shares or via SSH. At random times it drops all connections for another random period of time. The server still responds to ping commands.

Other than a lot of smbd_audit entries, I'm not seeing anything in syslog and nothing in dmesg.

Anyone have any clues as to where I can start looking? I am thinking of adding another network card, just in case it is the card itself that is bad.

Thanks,
Westley

---

### Post by Westley on 2016-12-24
Not sure what the issue was. Did a release upgrade to 16.04 LTS and now everything is working as before.

Even seems as if it is working faster than before.

---

