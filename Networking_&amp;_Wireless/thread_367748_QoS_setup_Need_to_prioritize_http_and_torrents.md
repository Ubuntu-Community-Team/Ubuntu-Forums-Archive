---
title: "QoS setup? Need to prioritize http and torrents"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by hotani on 2007-02-22
I know some routers are better at this than others, and there is a [d-link router](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=252069) that apparently handles it well--for $120.

But is there something either in ubuntu or azureus that will allow me to "nice" the torrent software so it does not completely kill my bandwidth when I'm trying to use it for anything else?

It would be nice to be able to just sit down and have normal intertubes speeds without having to kill azureus first. :(

---

### Post by esaym on 2007-02-22
Hmm.  If you are just trying to control the bandwidth on one computer that has bit torrent running couldn't you just limit the max upload of bit torrent?  If you are trying to implement this across a home network or something that is different, especially if your don't have access to all the computers.

I use a qos mod built into my firewall:

[http://community.smoothwall.org/forum/viewtopic.php?t=7922](http://community.smoothwall.org/forum/viewtopic.php?t=7922)

Which looks something like this: [http://lindsay.ath.cx/stuff/qosconfig.cgi.html](http://lindsay.ath.cx/stuff/qosconfig.cgi.html)

There is also a similar mod for ipcop.

There are also scripts that can do the same.  Search google for "wondershaper"

Details of QOS:
[http://lartc.org/howto/](http://lartc.org/howto/)
[http://lartc.org/howto/lartc.qdisc.html](http://lartc.org/howto/lartc.qdisc.html)
[http://lartc.org/howto/lartc.cookbook.ultimate-tc.html#AEN2241](http://lartc.org/howto/lartc.cookbook.ultimate-tc.html#AEN2241)

Have fun :)

---

