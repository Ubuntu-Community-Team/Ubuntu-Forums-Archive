---
title: "Ubuntu 20.04 persistent/permanent ip route and ip rule"
date: 2021-03-20
forum: Networking &amp; Wireless
---

### Post by pi-thrower on 2021-03-20
My question is the same as was asked here but never answered: [https://ubuntuforums.org/showthread.php?t=2394548](https://ubuntuforums.org/showthread.php?t=2394548)

What is the recommended way to make ip routes and ip rules persistent?  I've read in multiple sources what TheFu said in the above thread, that it can be done in rc.local.  Given that i only need one 'ip rule' and one 'ip route' command executed to accomplish what i'm going for this is certainly possible but i'd prefer to do this the way the developers intended, however that is.

I see that some static routing can be done in Netplan but it's more rudimentary than what i'm going for: [https://ubuntuforums.org/showthread.php?t=2394548](https://ubuntuforums.org/showthread.php?t=2394548)

I have a rule in IPTables that tags packets, a rule created with 'ip rule' to match on that tag and send those packets to a different routing table and i have the routing table itself.

---

### Post by The Cog on 2021-03-20
You used to be able to do that kind of thing in /etc/network/interfaces. 
This page echoes my thoughts: [https://askubuntu.com/questions/1080202/netplan-how-to-run-script-on-if-up-of-specified-device-only](https://askubuntu.com/questions/1080202/netplan-how-to-run-script-on-if-up-of-specified-device-only).
That contains a link to a FAQ with a solution (I haven't tried it): [https://netplan.io/faq/](https://netplan.io/faq/)
If you can't make that work, my next step would be a bash script in a cron job that checks every minute for the required rules and adds them if they're missing.

---

### Post by pi-thrower on 2021-03-20
> **The Cog said:**
> You used to be able to do that kind of thing in /etc/network/interfaces. 
This page echoes my thoughts: [https://askubuntu.com/questions/1080202/netplan-how-to-run-script-on-if-up-of-specified-device-only](https://askubuntu.com/questions/1080202/netplan-how-to-run-script-on-if-up-of-specified-device-only).
That contains a link to a FAQ with a solution (I haven't tried it): [https://netplan.io/faq/](https://netplan.io/faq/)
If you can't make that work, my next step would be a bash script in a cron job that checks every minute for the required rules and adds them if they're missing.

Yup, the answer was netplan.  The 'routes' and 'route-policy' parameters.  It's a bit weird to me that these are bound to interfaces as none of what i was trying to put in in terms of policy (match a mark set by IPTables) or routing (the routing table had one line, to set a default GW) necessarily married them to a specific interface.  This doesn't matter for my application however so i'll take the win.

See: [https://netplan.io/examples/#configuring-source-routing](https://netplan.io/examples/#configuring-source-routing)

---

