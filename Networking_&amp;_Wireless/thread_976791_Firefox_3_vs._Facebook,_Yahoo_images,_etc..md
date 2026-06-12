---
title: "Firefox 3 vs. Facebook, Yahoo images, etc."
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by missmaryrules on 2008-11-09
Whenever I try to access Facebook and Yahoo images, the pages load as if Firefox isn't rendering the sites' CSS style sheets.

[http://i38.tinypic.com/34y1r29.png](http://i38.tinypic.com/34y1r29.png)

[http://i38.tinypic.com/29mx5pk.png](http://i38.tinypic.com/29mx5pk.png)

At one point it was also loading Youtube the same way, but that seems to have stopped and is now loading properly. I've already tried completely uninstalling/reinstalling Firefox 3 as well as reverting back to Firefox 2 and still get the same results.

Oh, and the problem didn't start until my ISP assigned usernames and passwords to access their service. Any ideas?

---

### Post by spagaggum on 2009-11-13
I have this exact same problem..

I have a 9.10 ubuntu box and a vista box on a dlink dgl-4300 router.

After disabling EVERY possible piece of security on the router I finally found one that got my facebook back but not my yahoo.

NAT Endpoint Filtering.
UDP was set to Address Restricted.
TCP was set to Port And Address Restricted.

I set them both to just Address Restricted and I can now use facebook again..

Tho oddly enough my vista box with either setting can see all the pages just fine..

I don't know if this has any relevancy to the problem but hope it may help something cuz I know there are others out there with this problem.



And for some reason I can't post on this forum on my linux box either..
Keeps saying there isn't a msg in the box and this is the 12th time I've retyped it.

---

### Post by spagaggum on 2009-11-14
Oyeah I'm back.

Ok once again I don't know what I'm doing but this info may help..

I was trying to get my linux box to see my vista shares via my network and I changed a file and now not only can I see my network drive but facebook, yahoo mail, and all the other sites I had problems with the css sheets... NOW WORK!!

I did the whole gksudo nautilus thing and went to /etc/samba and in that folder was smb.conf
Make a backup of it and I went to the line that said
"name resolve order = hosts bcast"
I simply changed that to
"name resolve order = hosts wins bcast"

By adding wins to it I can see and access my network shares, and after a reset my yahoo mail, facebook, myspace, youtube and everything else works now.

Hope this might help..
Also here in Iraq I use a dsl or pppoe network so I gotta use a name/pass to get online as well.

Hope this helps in some way... good luck

---

### Post by Pellidon on 2009-12-13
Back sometime during 9.04 I lost images from some yahoo pages. I upgraded and it stayed the same. I looked at the preferences for Firefox and in the allow all images exceptions, yahoo was blocked. I removed the block and it works fine. Don't know if I twitched on a block request or if it was a firefox glitch.

---

