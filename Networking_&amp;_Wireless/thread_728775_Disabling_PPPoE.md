---
title: "Disabling PPPoE"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by omario on 2008-03-19
I've browsed around a bit and haven't found any solutions, so here I go...

I have a laptop with which I connect through a router to the internet. I set up the PPPoE on the router with no problem, and everything works perfectly fine. I am a college kid, so I am back and forth between home and school, and I take the router with me. Therefore, the desktop computer at home connects through the router when I am home, and directly to the modem when I leave for school.

Yesterday, I installed Gutsy onto it, and, since I was behind the router, everything was fine. But, as I am leaving back for school at the end of the week, I knew the computer would connect via the modem again, so I began to search for how to set that up. The solution there was "sudo pppoeconf" and I got that set up perfectly fine also (I am connected to it right now). My parents are not computer-literate, so I set it up to connect at startup.

Once everything was set up and I was pleased, I connected the router again, and the wireless connection on the laptop was happy, but the desktop refused to connect. I quickly gathered that it was still trying to connect to PPPoE connection, which was not working.

So...
- How do I revert back to the way it was before pppoeconf, or at least prevent it from trying to connect at startup?
- I am planning on just enabling/disabling via pppoeconf whenever I leave/come home, but I was just wondering if there was a better way to go about this?

Hope there's plenty of information there, and thanks in advance for any and all help.

---

