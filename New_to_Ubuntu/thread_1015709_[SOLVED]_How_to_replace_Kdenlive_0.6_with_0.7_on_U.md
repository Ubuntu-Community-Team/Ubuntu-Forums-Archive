---
title: "[SOLVED] How to replace Kdenlive 0.6 with 0.7 on Ubuntu 8.10?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by resander on 2008-12-19
I installed Kdenlive 0.6 from Synaptic Manager. A newer version 0.7 is available, but not via Synaptic. I put deb [http://ppa.launchpad.net/tpikalek/ubuntu](http://ppa.launchpad.net/tpikalek/ubuntu) intrepid main in /etc/apt/sources.list and issued: 

 sudo apt-get update
 sudo apt-get install kdenlive

after having removed Kdenlive 0.6 via Synaptic manager.

I expected Kdenlive 0.7 to be installed, but the old version Kdenlive 0.6 is coming back instead.

What do I need to do to get version 0.7?

---

### Post by Partyboi2 on 2008-12-19
I cannot find kdenlive listed from that repo. You sure its the correct one?

---

### Post by billgoldberg on 2008-12-19
This is the repo:

deb [http://ppa.launchpad.net/baudm/ubuntu](http://ppa.launchpad.net/baudm/ubuntu) intrepid main

Taken directly from [www.kdenlive.org](www.kdenlive.org).

---

### Post by resander on 2008-12-19
Thanks - the repo detail tpikalek changed to baudm only minutes/hours ago!

Installation of 0.7 now works.

By the way, Kdenlive is a Video editor. Looks good, but have not tried it yet.

---

