---
title: "Linux Networking support for ThinkPad T540p WiFi card options"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by mdlueck on 2013-11-13
We are interested in loading Xubuntu 14.04 onto a ThinkPad T540p when they are available.

As far as WiFi card options, I see listed:

[LIST]
[*]ThinkPad Wireless 2 x 2 BGN+ BT 4.0
[*]Intel Centrino 6235 (Jackson Peak 2 AC) 2 x 2 ABGN+ BT 4.0
[/LIST]
Both of those cards offer G and N WiFi connectivity. Any thoughts on the drivers available for Linux for both of those cards?

---

### Post by chili555 on 2013-11-13
> ThinkPad Wireless 2 x 2 BGN+ BT 4.0There is not enough information here to advise you. Is it a Realtek, a Ralink or a ... what??> Intel Centrino 6235 (Jackson Peak 2 AC) 2 x 2 ABGN+ BT 4.0Perfect support out of the box for all recent Ubuntu versions up to and including 13.10. I expect the same will be true in 14.04.

---

### Post by mdlueck on 2013-11-13
> **chili555 said:**
> > Intel Centrino 6235 (Jackson Peak 2 AC) 2 x 2 ABGN+ BT 4.0 Perfect support out of the box for all recent Ubuntu versions up to and including 13.10. I expect the same will be true in 14.04.

Thank you, we will head down that path in that case.

I was leery about "Centrino" being code for "Windows postured"... like the old WinModems years ago.

---

### Post by chili555 on 2013-11-14
Perhaps I should have mentioned this previously, but some Intel N cards coupled with some router's implementation of N, don't play well together. The easy but somewhat undesirable work-around is to disable N speeds in the driver. Most people don't really stream Blu-ray quality video to a laptop, so it's not a real issue for most. However, I understand that people do want to see that impressive 300Mb/s capability.

My recent Linksys AC router and my two Intel wireless devices work perfectly well in every Ubuntu version I've used, which is many.>  "Windows postured"... like the old WinModems years ago. Code, I'm sure, for cheap soft-modems.

---

