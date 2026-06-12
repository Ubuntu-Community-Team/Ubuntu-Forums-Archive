---
title: "Detecting network path failures"
date: 2022-03-31
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2022-03-31
Dear All,

I have two internet connections from an ubuntu router, and it all works ok with multiple routing tables so i can source route some networks.

I also have a script which does nslookups  down both routes to detect if the path is still good. I then use the results of this to switch default routes as appropriate.
I can't help feeling  the functionality of this script is part of the core ubuntu, but i cant find it.

Is there any built in functionality built in to ubuntu (22.04) to detect  if a network path is functioning and if not change the routing tables? BTW. I have don't  access to do an api call to test further down the network.

Thanks
Andrew

---

### Post by The Cog on 2022-03-31
I'm not clear on how your script is working, but I don't think anything like that is part of core Ubuntu. 

The nearest thing I know of is to run a routing protocol between your Ubuntu and the routers it is connected to, but that would require the cooperation of those routers which from an ISP is very unlikely. frr seems to be the package for Ubuntu if you want to implement those protocols. [https://frrouting.org/](https://frrouting.org/)

---

### Post by Andrew_Welham on 2022-03-31
Thanks,
All my script does is to fire nslookups (from a list of popular domains) at the ISPs dns servers (with routing rules to ensure the access is only available down the correct connection). Then if more than X concurrent dns lookup failures occur across the ISPs dns servers , the link is assumed to be down and the default route is changed. The script can continue to check (as static routing rules are in place) and then after Y successful concurrent lookups occur we flip back(still need to write that part)

Its real simple, but effective. Just feels a little hacky.

---

