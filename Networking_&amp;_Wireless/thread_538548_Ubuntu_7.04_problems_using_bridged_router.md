---
title: "Ubuntu 7.04 problems using bridged router"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Frosteh on 2007-08-30
I have a Zyxel SDSL router which is setup to use bridge mode, connected to it is a firewall behind which is my main network, the firewall is setup to use the first static IP address and has been working fine.

I built a 2nd box with Ubuntu 7.04 on it, connected it to the router on the 2nd network port, set it up to use our 2nd static IP address, put in the DNS servers, the gateway etc (using the GUI) and browsed and sent email just fine.

After coming back from a holiday I found it was mis-behaving, in fact it cannot access the outside world at all, it can't even ping the gateway at our ISP.  However networking is still possible in fact I can connet to the box from our internal network, a traceroute shows that the Zyxel kit is actually piping connections directly from our firewall straight through to the Ubuntu box, rather than sending packets out to the ISP only for them to come back (which I thought was neat)

I confirmed the same setup with a laptop using XP with the exact same network settings and that connects through to the ISP just fine.

So I know this is just a config problem on the box I just dont know where to look past the basic settings, I'm a total linux n00b to be honest, this is my first time using Ubuntu.

Any help much apreciated.

---

### Post by Frosteh on 2007-08-30
Is there an easy way to completely reinstall networking or reinstall the network card.  Thing is this was fine when I first set it up and something must have been changed which broke it.  I dont want to go through a complete reinstall that would be silly.

---

### Post by Frosteh on 2007-08-31
Bump

---

### Post by Frosteh on 2007-09-03
Anyone?

C'mon this should be a simple thing to setup, I can't believe it's so difficult!

---

