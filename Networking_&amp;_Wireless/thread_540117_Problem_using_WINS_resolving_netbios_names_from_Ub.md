---
title: "Problem using WINS resolving netbios names from Ubuntu to Ubuntu."
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by BrendanM on 2007-09-01
Ok, so here's my situation. I'm on a university network that uses WINS servers for name resolution. I have 2 windows XP machines and 2 ubuntu ones.

I have added wins to /etc/nsswitch.conf as well as /etc/samba/smb.conf and installed winbind.

I am able to ping my Linux machines by name from my Windows machines, and I can ping my Windows machines by name from my Linux, but when I try to ping one Linux box from the other one, I can only do it IP address. Name resolution doesn't seem to work.

In summary, Ubuntu->XP = fine, XP->Ubuntu=fine Ubuntu->Ubuntu=Nothing!

Does anyone have any idea what could be going on here?

 I know that a windows server makes 3 entries to a WINS server, I wonder if there's some difference about the way Ubuntu identifies itself that causes this issue.

---

