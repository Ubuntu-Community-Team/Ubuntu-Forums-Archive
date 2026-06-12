---
title: "Ubuntu + Samba + 3 XP boxes = Kaboom!"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by krelkor on 2008-01-03
Hey guys, i know everyone asks this but i still cant seem to figure this out after trolling through the forums

I have 1 ubuntu server using samba to share 1 mount point
As of last night, it was perfect, and could read/write from 2 windows laptops either on ethernet or wirelessly

This morning i hooked up a third windows box, and suddenly all 3 windows machines cannot see the ubuntu shares

i try to type \\server to connect to it, but i get nothing. All 3 computers are in WORKGROUP and can ping the ubuntu box just fine. 

Update, after a restart, i was able to connect to \\server on 1 laptop, but not the other 2

what exactly is going on?

---

### Post by krelkor on 2008-01-03
Since i have changed nothing on the samba installation files, is it possible there is something else happening? firewall maybe? or is samba not affected by the default firewall

---

