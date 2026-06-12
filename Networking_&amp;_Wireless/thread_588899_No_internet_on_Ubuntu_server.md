---
title: "No internet on Ubuntu server"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by andrewheiss on 2007-10-23
After upgrading to Gutsy and messing with some Apache and Hamachi settings, everything on my Ubuntu server has been going fantastically well until yesterday when out of nowhere I can't get an internet connection. I can get on my server through SSH, but I can't get the server to connect to anywhere (apt-get and lynx don't work, pinging outside sites times out). I'm a newb with all this dns and ifconfig stuff, so how do I go about diagnosing and fixing this problem?

Thanks!

---

### Post by TorchlightJay on 2007-10-23
hmm, so connecting to the server works fine but you can't browse with it. Are you sure it's not the network? Or what do you remember doing between the time it was last working and when it stopped working.

---

### Post by andrewheiss on 2007-10-23
Yeah - I have the server on local network behind a linksys router. My wife's XP machine stopped getting a connection yesterday, so we reset the router and she got back online - the server apparently never did. 

I poked holes in my router to allow ssh and apache and can get on just fine. My wife can get online just fine, so the router is working - there's just no outside internet connection from the server

---

### Post by andrewheiss on 2007-10-24
Still no outside connection. I can get to it from my local network at 192.168.1.100 and from the internet when I forward the ports on my router, but the server refuses to make any external internet connection. Any suggestions on how to fix this? It's kind of like pretty much necessary

---

### Post by andrewheiss on 2007-10-24
It's fixed! Apparently my ISP changed DNS servers or something, since my wife's XP connection died at the same time - I added OpenDNS's servers to resolve.conf:

208.67.222.222
208.67.220.220

and I can now browse happily with lynx, apt-get works, and hamachi does too! Wahoo!

---

