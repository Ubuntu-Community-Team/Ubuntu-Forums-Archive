---
title: "Failed to Fetch AND no servers found"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by uberdonkey5 on 2008-08-08
installing or updating software is not working...
I get Failed to Fetch... etc etc etc

I've checked countless pages and none solve my problem.
- I have enabled every repository I can see (using the gui, not by directly editing the file)
- I AM connected to the internet (using same connection to write this)
- when I try 'select best server' I get "no suitable download server was found"

I am connecting through a proxy in the office (maybe this is the problem?) However when I used gutsy gibbon (I upgraded to Hardy Heron) this connection was fine.

Any thoughts? (PS. I am relatively new (few months) to linux and pretty clueless about network connections). Thanks

Ian

---

### Post by uberdonkey5 on 2008-08-08
OK, seems it was to do with the proxy.

I had only set up the proxy server to operate with FireFox (edit/preferences/advanced/settings)

What I SHOULD HAVE done is gone into system/control centre/internet and network/network proxy

and changed the proxy settings there.
Basically I could access internet cos firefox was using proxy, but update manager etc was not.


(if you don't have control centre go into system/preferences/main menu to activate it on your menus)

Hope this helps others
Ian

---

