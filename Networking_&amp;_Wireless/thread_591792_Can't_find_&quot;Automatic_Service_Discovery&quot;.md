---
title: "Can't find &quot;Automatic Service Discovery&quot; checkbox in Gutsy Gibbon"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by dhalbert on 2007-10-25
I would like to disable avahi in Gutsy Gibbon. There are ways to do this by changing config files, but the easiest way I have read to do this is to uncheck "Automatic Service DIscovery" in the System->Administration->Network->General(tab).

However, I have no such checkbox in that tab. Was this checkbox removed from Gutsy? Or is this perhaps because I have no wireless networking on this desktop machine? ( I need to turn off avahi so that the ".local" domain is not treated specially. I have a VPN to an internal network that uses that domain.)

I can always fiddle with the config files, but I am bit mystified about the missing checkbox.

Thanks,
Dan

---

### Post by spd106 on 2007-10-25
I agree it is strange that it was there for such a short time. I suppose because it wasn't used very much and few people even knew what the difference was, they decided to removed it. To be honest there's was no real need for it to be there, it's not like you'll be needing to turn it on/off very often.

If you still want a gui based method of disabling avahi, then try using System -> Admin -> Services. Just untick the box next Muliticast DNS service discovery.

---

