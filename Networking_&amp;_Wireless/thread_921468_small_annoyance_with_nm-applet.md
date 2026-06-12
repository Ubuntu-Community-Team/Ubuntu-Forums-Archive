---
title: "small annoyance with nm-applet"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by jody.palmer on 2008-09-16
I'm using Gutsy (7.10 kernel 2.6.22-14-generic) and I have a small problem with nm-applet.

I once accidentally clicked on my neighbor's network and ever since then, nm-applet will automatically connect me to the neighbor's instead of my own - I must manually choose my own ESSID.

I suspect that the neighbor's ESSID is stored in a list in some config file and that simply deleting it will solve the problem, but I can't find that config file.  (The keyring only contains keys for networks that are encrypted, and my neighbor's is open - thus, I cannot find it in the keyring.)

Does anybody know where nm-applet stores such information?

---

### Post by jody.palmer on 2008-09-16
I just found it... it is a directory beneath ~/.gconf/system/networking/wireless/networks

I hope nobody wasted any time on this.

thanks

---

