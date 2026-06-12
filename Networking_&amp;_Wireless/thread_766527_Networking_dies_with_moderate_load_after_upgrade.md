---
title: "Networking dies with moderate load after upgrade"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by maethor on 2008-04-25
After upgrading to Hardy, I've found that both wired and wireless networking will die soon after I start to put a moderate load on the network (such as web browsing or a NX session).

Upon startup everything works - the wireless connects to the right access point and both wired and wireless networking can get IP address. I am able to ping various servers and make SSH connections into them. Once I fire up firefox or start the NX client, within a minute or two networking stops working. Killing firefox or the NX client doesn't bring networking back. There's nothing in dmesg to indicate any problem. I've tried wireless only, wired only and both running at the same with the same results.

Any ideas?

---

### Post by zensmile on 2008-04-25
I am getting similar results. Networking just goes in and out without warning. I have tried turning roaming off and on, using a supported USB wifi adapter and a wired connection, and logging on and off. The internet connection just dies. Weird.

I am a total newbie to this whole linux thing. I have updated with the package manager (when internet was working well), so I do have up-to-date install. Maybe someone has a solution?

---

