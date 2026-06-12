---
title: "WOL stops when bridging"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by jrccsi on 2007-08-11
I'm stuck! I have a headless fiesty box running in a back room as an encrypted file server. I had WOL working perfectly, but then I started playing with VirtualBox (BTW, working great!) In the process of setting up my VM images I needed to setup bridging. Now that I have bridging turned on WOL will not work. If I edit my /etc/network/interface to exclude the bridging then I can WOL the system. Ethtool shows wol enabled, it's setup in the bios correctly. I tried removing the bridge during shutdown but that did not seem to solve the issue. Only after removing bridge setting, booting, then shutting down it worked. 

Thoughts?

---

### Post by heinzie on 2008-01-10
Same problem here. Unfortunately I haven't been able to solve it, so I used a 2nd nic for the bridge.

---

