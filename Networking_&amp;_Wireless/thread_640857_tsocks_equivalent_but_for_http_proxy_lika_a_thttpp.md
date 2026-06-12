---
title: "tsocks equivalent but for http proxy lika a thttpproxes"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by darck on 2007-12-14
Is there a program similar to tsocks but for http proxies? Application which can simulate internet connection for programs which can't use http proxy.

Another question:
XMMS last.fm plugin works only when XMMS is run from console. It doesn't work when i lunch xmms by pressing shortcut button on taskbar. Purpose of plug-in is sending information to last.fm server. It has to use proxy server when it use port 80. Any idea why it's working in console only? 

The same is with another last.fm plugin in audacious program - works only when runf from console.

---

### Post by hl2040 on 2008-05-10
Regarding tsocks equivalents, there exists a package called vtun which is a much more robust solution that tsocks. It's harder to setup, it appears, I haven't used it, but it doesn't try to hijack your applications' connect() function calls, it actually just creates a virtual network adapter which exists on both sides of the tunnel you want to setup.

Regarding lastfm:
Browsing the ubuntu/debian archive for proxies, I noticed a package called 'lastfmproxy'. I haven't thought too much about your lastfm problem, but maybe that could help.

---

