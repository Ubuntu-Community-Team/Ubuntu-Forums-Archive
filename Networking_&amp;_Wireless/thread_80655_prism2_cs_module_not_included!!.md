---
title: "prism2_cs module not included?!?!"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by mjwood0 on 2005-10-22
I'm very confused...

I have a Senao/Enginus NL-2511 PLUS EXT2 PCMCIA card for my laptop.  When I insert it, Ubuntu somehow decides to load the Orinico drivers (as other people have mentioned).

First of all, this is stupid.  There is an existing bug (#18062).  However, the developers seem to think that since the Orinico drivers sort of work, it's not a huge problem...  let me tell you that for me, they don't even sorta work.  I get dropped connections constantly with them.

I also notice that the prism2_cs module is not available.  I thought the wlan-ng drivers were included in the Kernel for 2.6.12.  If so, did they just not build the _cs version?

I see this topic has been sorta beat to death, but I was just wondering if anyone has figured out how to get away from the orinico_cs module and to the prism2_cs module.  Heck, even hostap_cs would be a step in the right direction.

It's odd that Intersil Prism is one of the few companies where they release their design to the open source community and there are still driver headaches....

---

### Post by srf21c on 2006-10-16
Having the same issue with a 2511-CD plus pcmcia card and Xubuntu dapper 6.06.  Tried blacklisting the orinoco_cs driver in /etc/modprobe.d/blacklist which will allow the hostap_cs module to load, but I'd still prefer to use the proper prism2_cs module.

---

