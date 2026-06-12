---
title: "BCM4318, ndiswrapper, wicd ip obtain takes forever"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by Donner87 on 2007-07-28
I followed a page in the wiki that described how to get a BCM4318 wireless card working ... this is after having followed many, many HOWTOs in this forum trying to get my wireless working. Wireless has worked from time to time, but kept breaking and i keep trying different things but to no avail :/

Anyway, so I followed the post which had me uninstall the network manager and ndis, and then reinstall ndis from the latest source. I did that, and installed wicd like it said. I rebooted, blah blah blah and long story short wireless is working ... for now, but there's a problem. Wicd takes *forever* to obtain an IP address. I read some posts about Obtaining IP Address hanging on WPA enabled connections. In my case it hangs for 3 minutes and then finally works.

Any ideas on how to fix that issue? Assuming wireless will still work the same way after a reboot ....

Thanks!

---

### Post by ugm6hr on 2007-07-28
Don't know - I don't use ndiswrapper, but it is worth asking in the Wicd forum:
[http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)

Might be worth including information on what happens if you take the security off the router (i.e. remove WPA), since it is possible the issue is WPA.

Also - have you tried the different wpa-supplicant drivers?  wext seems to work for most (rather than ndiswrapper).

---

