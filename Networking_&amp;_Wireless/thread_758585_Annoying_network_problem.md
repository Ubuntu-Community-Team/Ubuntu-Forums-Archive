---
title: "Annoying network problem"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by steve.rumsby on 2008-04-18
I've just installed my first Ubuntu 7.10 system on a laptop. All works fine apart from the network. I have a DSL router with both WiFI and wired connections, and get the same behaviour from both. Naturally Windows machines connect flawlessly...:-(

I have the network interfaces configured for DHCP, and they will happily get all the necessary settings from the router (IP address, netmask, gateway & DNS). DNS lookups work fine (the router is the DNS server). I can ping internal and external hosts, so IP connectivity in general, routing, etc.  is OK. I just can't do anything *except* ping. No HTTP, no telnet, no SSH. Nothing else works.

I've seen other threads that talk about IPv6 issues, specifically with Dlink routers, causing similar symptoms. I've tried some of the fixes from those threads with no success.

Any ideas? All suggestions gratefully received...

Thanks,
Steve.

---

### Post by steve.rumsby on 2008-04-18
Never mind. A bit more digging around found another thread in this forum that pointed me to this article:

[INDENT][http://articles.techrepublic.com.com/5100-1035_11-6174075.html]("http://articles.techrepublic.com.com/5100-1035_11-6174075.html")[/INDENT]

The fix there solved the problem, with one minor tweak. The parameter is called tcp_window_scaling in 7.10, not tcp_default_win_scale as in the article.

So, 

[INDENT]echo 0 > /proc/sys/net/ipv4/tcp_window_scaling[/INDENT]

fixes the problem immediately, but goes away on a reboot while editing /etc/sysctl.conf and add:

[INDENT]net.ipv4.tcp_default_win_scale = 0[/INDENT]

makes the fix persistent.

Steve.

---

