---
title: "VPN connection unstable"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by pangel on 2008-03-01
Hi,
My VPN connection breaks every 5 minutes. I'm connecting to a Cisco concentrator (on a university campus). The problem is the same whether I use vpnc or the proprietary software vpnclient.

There is no such problem when I dual-boot on windows xp, so I assume it's not a connectivity issue.

Both vpnc and vpnclient do not notice anything special - firefox just starts hanging on "Looking up for server.tld" and ends up with a "Unable to find the proxy server" (I use a proxy to access Internet through the VPN concentrator, but when the problem occurs I can't access the local network of my concentrator either). 

Killing the processes and reconnecting to the concentrator always fixes the problem for 5 new minutes.

I'm connecting with an ethernet cable (if that matters). Also, this is a fresh Ubuntu install and I did not change any route configuration or anything.

---

### Post by astroclast on 2008-03-01
I have a similar problem, though a little more rough.  I'm using VPN to access journals when I work off campus.

Although my connectivity seems to be robust, when I actually try to download a PDF file from one of those journals, my Ubuntu laptop freezes and I have to reboot the hard way.  I've tried this with Firefox 2.  I switched to firefox 3 to avoid this and after a short period of success and happiness, I now have the same problem.

For various reasons I suspect it is a problem with Ubuntu.  Does anyone have a similar experience?  Or an answer?

Thanks.

---

