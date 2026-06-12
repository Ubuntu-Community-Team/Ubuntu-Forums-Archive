---
title: "Throttle network traffic on the local machine"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by Onion Avenger on 2007-08-22
My laptop (running Feisty) shares a DSL Internet connection with some other computers.  The problem is that our DSL connection has a max download speed of about 160 KB/s to share amongst several machines.  If I am downloading something, say, a video off of YouTube, then I hog nearly all 160 KB/s while everyone else finds their Internet slowing to a crawl.

What I'd like to do is to throttle my own bandwidth so I download at some set maximum, such as 100 KB/s, so my Internet usage doesn't interfere with the others sharing my connection.

Searching Google and the forums have led me to some tutorials on configuring iptables or other things but those solutions are far too advanced for my needs.  I'm not modifying rules on some router, this is a localhost issue.  I think I need to use the "tc" command but I'm a little unclear on what exactly this should be.

Any help?

---

### Post by jakev383 on 2007-08-23
I normally do all of this on the router level, but here's a couple that may help you.  Never used trickle myself:
[http://www.linux.com/articles/61293?tid=100&tid=47&tid=13](http://www.linux.com/articles/61293?tid=100&tid=47&tid=13)

These I've used before - you'll need to adjust them for your ports and protocols:
[http://www.howtoforge.com/voip_qos_traffic_shaping_iproute2_asterisk](http://www.howtoforge.com/voip_qos_traffic_shaping_iproute2_asterisk)

If you are only concerned with doing this while downloading and happen to be able to use the CLI command wget, it has a flag to limit the download speed.
Hope that helps some.

---

