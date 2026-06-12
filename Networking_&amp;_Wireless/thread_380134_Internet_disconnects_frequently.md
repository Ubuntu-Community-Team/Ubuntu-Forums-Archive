---
title: "Internet disconnects frequently"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by rup on 2007-03-09
I am running *Ubuntu 6.06 LTS- the Dapper Drake*. I configured the adsl connection using **pppoeconf**. After connecting using **pon dsl-provider**, the connection lasts for about 15 mins, and then, to get back onto the internet, I've to reconnect using the same command.

After the connection has tripped on its own, if I use **poff -a** I get the following output:
*/usr/bin/poff: /bin/kill failed.  None stopped.*

and, **plog** doesn't show anything. Whereas, in a disconnected state plog is supposed to show the last session stats, ending with the line 'Exit'.

I scoured the forums for a solution, but in vain. Some posts are for specific routers and drivers, but my hardware works fine on Fedora6 and WindowsXP. According to one post, I made the following changes to the **/etc/ppp/options** file:

[I]changed auth to noauth
set the lcp-echo-interval to 0
set the lcp-echo-failure to 0[/I]

I edited Firefox configurations to *disable ipv6*.

Nothing worked.

Can somebody help?

---

