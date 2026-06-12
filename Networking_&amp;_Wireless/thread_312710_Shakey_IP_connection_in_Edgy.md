---
title: "Shakey IP connection in Edgy"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by zappa420 on 2006-12-04
Hey all I've got a network problem thats been stumping me for sometime now.
I'll be browsing the net and all of a sudden I can't get anywhere.  I can ping any ip address that I want while browsing is still crapping out on me.
I was having the same problem using SMB sharing and tried using FTP and that would timeout on me as well.  The time outs can last as little as 10 secs to 10 minutes.  I've manually added the Opensource DNS to my /etc/resolv.conf and to my router as well.  So I'm pretty sure it has nothing to do with DNS.  I've tried static as well as dynamically setting my ip address.  When I'm having the problem I can't even get into my router thru Firefox or Konqueror.  
I think I've removed most traces of IPv6 from my system.  I'm at a loss for what else I can do.  

I've got a WUSB54G v.4  adapter.  I can run downstairs to my windows box while my Edgy networking is choking and everything is smoothe.  I didn't have any problems like this in Dapper.  I can play Savage (an online game (open source now)) and I've got a great ping and don't seem to ever have connection issues. Downloads will stall on me though.  

So it appears that if  I restart the network with /etc/init.d/networking restart it gets me going again right away.

Any ideas on why its working one minute and not the next.  Thanks for reading all this.

Zappa

---

### Post by zappa420 on 2006-12-15
shameless bump for help:confused:

---

