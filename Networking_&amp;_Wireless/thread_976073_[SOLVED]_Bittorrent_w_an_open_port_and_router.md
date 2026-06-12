---
title: "[SOLVED] Bittorrent w/ an open port and router"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by jakenbake42 on 2008-11-09
I am currently trying to use Transmission and get some bittorrent files
but I'm having trouble downloading anything
It just says not enough data
0 peers avaiable
and the download amount stays at none out of [file size]
and when I went to the preferences it says listening port is open
So is it something with my router?
I've tried like 6 different torrents for the same file
thanks in advance

---

### Post by yudelevi on 2008-11-09
It could be the torrent itself, try getting a more widely spread torrent (like ubuntu for example - [http://torrent.ubuntu.com:6969/file?info_hash=3%82%0D%B6%DD%5EY%28%D2%3B%C8%11%BB%AC/J%E9L%B8%82](http://torrent.ubuntu.com:6969/file?info_hash=3%82%0D%B6%DD%5EY%28%D2%3B%C8%11%BB%AC/J%E9L%B8%82) ) and report if this keeps appearing.

The other solution would be to sniff traffic and see where things go wrong, a good solution would be to enable UPnP on router and use UPnP in transmission, this should make this work as well.

---

### Post by jakenbake42 on 2008-11-09
ah silly me
that worked
thank you very much

---

### Post by jakenbake42 on 2008-11-09
actually ok this might just be me but
so the ubuntu torrent worked
but I get the same not enough data and 0 peers when I try anything else :(
but i have yet to try enabling UpnP or whatever it is on the router
I will when I have time and write back

---

### Post by tylermenezes on 2008-11-09
Seems you're just not getting popular torrents, then. Does the site you're downloading it from have any statistics on the number of seeds and peers? Another possibility is that it's a private tracker.

---

### Post by jakenbake42 on 2008-11-11
Yeah I'm not sure but I guess I'll just have to tinker with it
thanks a lot for all the help

---

### Post by jakenbake42 on 2008-11-15
Just wanted to say thanks to everyone for all the help
but heres what's up currently
Can't even download really non-popular files
and most files download incredibly slow
i am behind a router with a wireless connection [fast browsing but its got like a 17% connection] 
any help on improving download speed and accessing more files?
Would making the connection wireless help a lot [im assuming yes]?
Thanks in advance

---

