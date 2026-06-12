---
title: "ntp server question"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2008-03-30
Hi Folks,

i have just clicked the button for automatic time synchronisation in my clock (since last night the change from summer to wintertime occured and my ubuntu did not notice it).

that went well, and now the lock is running perfect. However, now i seem to have a ntp server running. That is not really a problem for me, but i really do not like it's behaviour. 

so here is my question:
**How can i forbid ntpd to listen on any/all interface(s)**. I only want it to query! This is a laptop i carry anywhere and i do NOT want any more open ports that i have to have ! I don't see any reason for ntpd to bind to all interface it can find. (if it has to bind, then it can use the loopback) 

I know how i could suppress access to these ports via iptables, but that is NOT the desired behaviour. Also, it is very nice that it binds to the ipv6 ports - but i don't need it. How do i tell it to only use ipv4 ?

any help would be greatly appreciated

---

