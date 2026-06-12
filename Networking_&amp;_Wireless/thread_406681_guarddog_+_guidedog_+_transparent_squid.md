---
title: "guarddog + guidedog + transparent squid"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by nardus on 2007-04-11
Hi there.

I am using a machine with Ubuntu 6.04 as firewall + transparent proxy for work, and doing most of the configuration via guarddog and guidedog.

The thing is that it seems that g*dog do not seem to support the idea of a transparent proxying, and everytime I make any change in the firewall or routing settings, I have to re-enable manually the iptable rule that forwards traffic from port 80 to port 14080, the one where squid is listening.

How can I do so that I don't have to retype
"iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 80 -REDIRECT --to-port 14080" each and every time, so that it persists against guarddog and guidedog settings?

Thanks in advance. I hope I was clear enough, and that someone out there is able to help.

Regards,

I.-

---

### Post by guysmiley25 on 2007-05-07
This is also something I would be interesting in knowing about. I have not got as far as you yet but my cheat would be to create a script like so.

```

#!/bin/bash
gksu guidedog
gksu iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 80 -REDIRECT --to-port 14080

```

And then use this script to run Gudiedog. Similarly with Guarddog.

Could I please ask, what does Guarddog do? Can you use it to block ports?

---

