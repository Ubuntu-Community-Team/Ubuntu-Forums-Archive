---
title: "Making all ubuntu connections pass through proxy"
date: 2019-03-27
forum: Networking &amp; Wireless
---

### Post by HexDump on 2019-03-27
Hi,

I have been playing with ubuntu configuration all day trying to set a system wide proxy without luck. My goal is to make all connections in the system to pass through a proxy. Or al least, if this is not possible make all connections not passing through proxy fail.

I have added the proxy configuration to /etc/environments, I have set it in network settings too (ubuntu UI) and well, it works for firefox but for example apt is still connecting through my own ip not the proxy. On the other hand I need to configure Android Studio to use the proxy too. I know I can configure android studio proxy through its own settings but I don't want to configure every program with its own settings (Some programs have an option to use the system proxy but others doesn't).

Is there any chance to accomplish this?

Cheers.

---

