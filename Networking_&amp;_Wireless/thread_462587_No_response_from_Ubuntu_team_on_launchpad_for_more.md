---
title: "No response from Ubuntu team on launchpad for more than 1and a 1/2 months now."
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-06-02
I posted a bug/problem I have been consistently facing and the solution of which is very critical to me on launchpad on 04/21/07. SInce then I don't think any of the Ubuntu team members has replied. I have one response but that is from a user like me, not the tech team. It is always advised to do some research if a problem occurs, then post in this forum and finally post a bug ([https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108450)). I wonder why no one has paid attention to the bug I posted. Does anyone has any idea?

Keith.

---

### Post by spd106 on 2007-06-04
It was a good idea to open a bug report on launchpad, but the ratio of bug squashers to bugs is very low, so your experience is not uncommon. If you have a particularly urgent problem a better place to open a ticket is at [https://answers.launchpad.net/](https://answers.launchpad.net/)

A couple of things to try :

Check the /var/log/syslog for network manager error messages or at least identifying the point in the connection process that fails. This log file usually contains sensitive information (encryption keys) that you will want to remove before posting to a public viewable place.

Look for a firmware upgrade for your wifi AP.

---

