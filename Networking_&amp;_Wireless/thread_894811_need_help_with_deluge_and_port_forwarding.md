---
title: "need help with deluge and port forwarding"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by logos34 on 2008-08-19
I need to speed things up here, if possible, without compromising my security. Here's a screenshot of my current rates:

[ATTACH]82158[/ATTACH]

Upload reaches near max (the config wizard set the default at 9.0 KB/s), so that appears to be ok.  But can I increase these download speeds?  I'm currently on a 768 kbps down/128 up ADSL line, DHCP, PPPoE dynamic IP (yeah, pity me). I'm behind a wired D-link router, and I should apparently be port forwarding (posts 6881-6889), right?.  But what is the safe setting?  There's a windows XP machine on the router too, and I can't afford to risk any hacking (mine too!).  Firestarter tray icon is an angry red all the time, lit up with blocked hits.

Networking is the one computer subject I really HATE/bores me, I just want it to work.  The documentation on deluge is pretty sad, so can anyone walk me through this?  Is the 'virtual server' tab in the router config what I want in order to set up the forwarded port?  (screenshot below).

TIA

[ATTACH]82157[/ATTACH]

---

### Post by logos34 on 2008-08-19
anyone?

---

### Post by epidemiks on 2008-08-19
check portforward.com for your instructions to set your dlink to forward the ports deluge wants to use.
i don't think there's any risk regarding getting hacked..

---

### Post by logos34 on 2008-08-20
> **epidemiks said:**
> check portforward.com for your instructions to set your dlink to forward the ports deluge wants to use.
i don't think there's any risk regarding getting hacked..

portforward.com only has instructions for uTorrent and my router (di-604).  

I've gotten it to work ok (sort of) using the random ports default, with the up speeds at or near max and the down speeds at an acceptable level (I think the problem so far has been that I just seem to be in poorly seeded torrents), but firestarter is still going crazy, and slowly over time eating up more and more cpu cycles as the hits pile up (always the same port chosen by deluge).  Isn't there a way to fix this while continuing to use the random ports default setting?

---

