---
title: "Limit traffic to specific ip via linksys router"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Colemanvt on 2008-01-16
So here's the back story. I got a room mate he sucks at life at limiting his upload and download rates when utilizing a torrent download system. (kick my self for introducing him to it in the first place) I was wondering if there is any way I can limit the total traffic going to one ip so when he decides to download something it doesn't smash the internet connection on the rest of the network computers. Also I'm using a linksys wrt54g and a wrt54gl that I can pretty much interchange and I'm currently using hyper wrt firmare on the gl model.  Just wondering if anyone has any ideas...

thanks

---

### Post by chewearn on 2008-01-17
Some linksys router has a QoS set-up page, where you can set the priority of services.

---

### Post by Colemanvt on 2008-01-17
Thanks man for pointing that out I always passed over that tab for some reason guess I just didn't know what it stood for so just overlooked it.

So this is what I did...

enabled Qos

Got his mac addy from the DHCP client table

Input it on the Qos and put his priority to low/medium and turned my pc and my 360 which are attached to the switch part of the router to high.

Sound like that'll work?

So technically that won't limit him but if another device on the router needs b/w it'll cut his flow pretty much right?

---

### Post by chewearn on 2008-01-17
I don't personally know how the QoS is implemented in the firmware, but if it's working like it supposed to, then yes.  By putting your traffic at high priority while his at low, your traffic will always supersede.

---

### Post by Colemanvt on 2008-01-17
that's my hope because anything internet wise should have higher priority than downloading f'n country music... :-)

---

