---
title: "how do I determine my upload line speed?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-19
Just downloaded deluge... trying to configure it.  Usually I'm on a wireless connection.  Though I move between three or four frequently.  Can anyone tell me what speed I should enter here for best results?

---

### Post by Hospadar on 2010-02-19
You'll just have to play around with it, it depends a lot on your region, at first I would leave up and down speeds set to unlimited (typically 0=unlimited, I think that is the case with deluge).

Some ISPs will throttle your connection if you have any bittorrent going, somtimes I notice major speed changes if I have too much upload, or too much download.  Generally speaking though, you'll probably be fine with unlimited speeds in both directions since with the exception of extremely popular torrents your speed will be limited by the number and quality of peers rather than your ISP.

Another thing which is important that you do both for your connection speed and legal security is to set you client (deluge can do this, as well as any other modern bittorrent client I know of) to only allow encrypted connections both inward and outward.  You don't really need to worry about loosing peers by only allowing encrypted connections as all modern clients support encryption and have a preference for encryption enabled by default (At least all clients I know of).

This is also important for your download speed since it will be harder for your ISP to detect you are using bittorrent and thus throttle your connection (most ISPs don't really care what you are torrenting, or whether you are actually hogging bandwidth, so encryption can protect you from such throttling).

---

