---
title: "Persistant Intermittent LAN Failure 14.04"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by shag00 on 2014-06-26
Problem: Persistant (occurs every hour) intermittent loss of LAN connectivity.

LAN Overview: 2x Win 7 PCs on a workgroup connected to a Ubuntu 14.04 machine via Samba all connected via a router using wired connection. The Ubuntu machine acts as a server to the the Windows machines and Win PC 1 accesses the Ubuntu machine as a local Ubuntu user and Win PC 2 accesses the Ubuntu machine as a guest. The router also provides wireless connectivity to guests and smart phones.

Detail of Problem: After starting all the machines (sometimes more than once) they are all connected and operate smoothly, file transfers are possible both ways with appropriate permissions.

Within an hour connectivity is lost between Win PC 1 and Ubuntu, at this point Win PC1 cannot see and files on Ubuntu, however both Ubuntu and Win PC1 still have full connectivity with Win PC2. All machines normally still have access to the internet. At this time several variables may exist:
1/ Ubuntu can see the Windows Workgroup and can see files on Win PC1 (or not).
2/ The wireless network ceases to operate, when this occurs all network connectivity is lost. This occurs infrequently, once every 2 or 3 days.
3/ Internet connectivity of Win PC1 is lost (or not).

Other Information: I have used this setup on Ubuntu 13.10 for about 6 months without problems. I am not even sure it is a 14.04 problem as that has been installed for about 2 weeks (or a week before these problems surfaced). There has been no software added to the Windows machines recently while the Ubuntu machine has been fiddled with after the upgrade to 14.04 with new repositories and software, eg YPPA manager and VLC 2.2. Permissions were also changed in Samba but did not immediately cause this problem. 

I would describe myself as a Ubuntu beginner and the assistance I am after is quite low level in that I most need help in identifying what is causing the problem, ie how to troubleshoot it. I do not even know what reports/information I need to include with this post. I also understand that this may also be a Windows or router problem.

Thanks in advance.

---

### Post by shag00 on 2014-06-27
I have found the culprit, it is the screensaver in 14.04. Whenever it activates the LAN crashes.

---

