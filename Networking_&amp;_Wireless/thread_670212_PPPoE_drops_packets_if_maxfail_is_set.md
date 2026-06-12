---
title: "PPPoE drops packets if maxfail is set???"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by JasonWalton on 2008-01-17
I set up PPPOE using ppoeconf, and everything is running fine, but last night my connection dropped for some reason, and after 10 retries it gave up and didn't try to reconnect.

No problem, I think, I go edit my /etc/ppp/peers/dsl-provider, and uncomment the line:

  maxfail 0

And I reconnect with 'sudo pon dsl-provider'.  And, my internet is totally sucking.  I try to ping my ISP, and ping seems very sluggish and non-responsive, and is loosing between 25%-50% of packets.  Looking at my torrent client, I see 8k/s.  So I try commenting out that maxfail line again, and poff and pon, and everything is fine again, no packet loss, and ping is sending packets in a nice orderly fashion, BitTorrent is pulling down 200k/s (which is what it's throttled to).

It seems like if I insert the maxfail line, and set it to anything (I've tried 0 and 1000), I get terrible packet loss.  Any ideas?

---

### Post by JasonWalton on 2008-01-17
Ok, never mind.  Seems like it happens at random, and it was just coincidence that it was happening when I changed that setting (perhaps it's every second connect?)  I'll reset my modem and see what that does for me.

---

