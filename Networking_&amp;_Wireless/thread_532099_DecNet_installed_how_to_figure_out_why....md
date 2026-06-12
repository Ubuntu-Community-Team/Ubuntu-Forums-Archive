---
title: "DecNet installed? how to figure out why..."
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by ture_atlantis on 2007-08-22
recently i have noticed that on boot DecNet is being loaded.  i do not know of anything that i have installed that would use it.  is there a way to use dpkg or apt-get to find out what package installed it? also, how do i shut it down? ('/etc/init.d/decnet stop' does nothing)

it doesnt seem like its running, but it still starts at boot time - making me nervous.

thanks

---

### Post by sfarber53 on 2007-08-22
Did you buy your machine 2nd hand from and old DEC techie?  I can't imaging why those protocols would be loaded otherwise.

DECNET is huge (loaded size) and very inefficient compared to today's protocols.  In it's day, however, it was the Rolls-Royce of routed communications.

Yes, by all means uninstall it, but I'm sorry I cannot tell you how.

Cheers,

Steve

---

