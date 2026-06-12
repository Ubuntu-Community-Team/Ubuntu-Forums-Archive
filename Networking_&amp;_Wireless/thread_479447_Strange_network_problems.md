---
title: "Strange network problems"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by Tuffy on 2007-06-20
Hello :D I need some help with my network here.

Something strange happens with my network when I'm using Linux. This only happens when I'm using Linux, no problems with Windows at all. Whenever I try to download something inside Linux, it occasionally stops (dropping down to 0 KB/s ), and times out, in the middle of the download.

The problem is the same with both cable and wireless network, but it's only on the router I'm currently using. No problems with any other routers. And I don't want to buy another router, I want to fix this darn problem :p

The router is a D-Link DIR-635.

:popcorn:

---

### Post by conjur3r on 2007-06-20
Stay away from DLink.  At work, we've had issues where the dlink device would reissue ip addresses at random before they had run out causing intermittent network blackspots.  The model we have has hideously bad DNS relay support.  So bad so that it's been overrided and switched off.  When it worked, it worked for a little bit but then resets and name resolutions were broken.

The first thing you have to do is diagnose the problem.  When it next stops downloading, can you still browse the internet?  Try a different site you haven't browse to (to test the DNS) as it could be cached in your browser.  How frequent is it?

---

### Post by Tuffy on 2007-06-20
I can download 2 things at the same time, and suddenly one of the stops. the other one continues normally :(

I also noticed that when I try to reload the package data in synaptic, the exact sources at the exact  percent of the download stops all the time! :confused:

---

### Post by Tuffy on 2007-06-20
Nobody knows what I should do?

---

### Post by jii2 on 2008-03-04
hi,

anything new about this problem? did u find a solution?

thanks.

---

