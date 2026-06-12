---
title: "p2-233 w/ 128MB ram ok for firewall?"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by techboyjk on 2007-04-06
I need to setup a firewall that will act as a transparent bridge. I'm going to be using ubuntu, iptables, and bridgeutils. 

My question is, for a website that may do up to 10-20Mbps bandwidth, will a p2-233 with 128MB keep up? It will be a bare server install of ubuntu(no x windows or anything) 

I can up the ram if necessary.. I have 4 of these machines, and I'm wanting to setup a primary firewall, have another one, powered on, sitting right next to it incase the first one fails, have another one powered off in case the first two fail, and have the 4th as parts backup..

---

### Post by d.j.schroeder on 2007-04-06
Any particular reason you are going to use Ubuntu for that purpose?  What about using IPcop or Smoothwall.  The setup would be easier?

I haven't done what you're talking about with Ubuntu but I have done it with Smoothwall on a low end P3.  I don't think CPU usage ever saw much over 5%.  So you should not have a problem.

---

### Post by techboyjk on 2007-04-06
> **d.j.schroeder said:**
> Any particular reason you are going to use Ubuntu for that purpose?  What about using IPcop or Smoothwall.  The setup would be easier?

I haven't done what you're talking about with Ubuntu but I have done it with Smoothwall on a low end P3.  I don't think CPU usage ever saw much over 5%.  So you should not have a problem.

can i do layer 2 bridging with smoothwall or IP cop?

---

### Post by d.j.schroeder on 2007-04-07
I don't think so, at least not without making some modifications yourself, but you'd have to do that on Ubuntu as well.  I didn't notice bridgeutils in your initial post the first time I read it.  If you have to make modifications for that purpose it probably won't take any more to do it with Ubuntu than with anything else.  I still think your proposed computer should not have problems with those bandwidth requirements.

---

### Post by az on 2007-04-07
You would meet those requirements with a 386 machine.

Ubuntu will run fine.  You don't need more ram.  Most appliance routers you buy off the shelf at wal-mart run way under 100 MHz.

---

