---
title: "Dell 1749 wireless enable/disable"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by HowardJZ on 2011-02-24
I'm writing this up because the issue gave me some trouble. I can imagine others may have faced the same circumstance.

The Dell Studio 17 (model 1749) does NOT have a physical switch to turn on/off the WiFi. WiFi is turned on/off via the F2 key. ... Silly me ... I had net discovered this when a put Ubuntu 10.04 on it. Since it was turned on already, it just worked.

Somehow, still unknown to me, I managed to hit the F2 key and turn off WiFi. Because I was unaware that F2 turns on/off the WiFi, I suspected I had a broken WiFi thingie. ... Some diagnostic experimentation followed with some RTFM and I found the F2 thing.

Still, there's a problem. If you turn off the WiFi will running Ubuntu, although I could turn the WiFi back on (it shows Wireless Enabled) I could not get it to connect.

The solution is to assure that the WiFi card is ON, then reboot. Ubuntu will find it and use it.

That is all.

---

