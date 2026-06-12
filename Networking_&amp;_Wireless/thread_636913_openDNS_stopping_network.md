---
title: "openDNS stopping network"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by thered on 2007-12-10
There are a few other threads around but in reading them, IMHO, none have come with an answer, or at least not one an end-user like myself can understand anyway,

I had a perfectly good, working network. - two ubuntu machines and some freeNAS storage.

I was getting a little miffed with slow browsing that many have reported, the solution to this seemed to be, according to several threads, to use openDNS.  I duly set my router to the openDNS servers and yes, a noticeable improvement. Why? would be another question.

My network stopped working, refused to see any other machines or shares.  Returning my router settings to default got it up and running again.

So, is there a way to do both? 

Is there anything in the Ubuntu pipeline to improve the browsing issue? There seems to be many complaints about it.

---

### Post by fineas on 2007-12-10
How about disabling IPv6? check here [http://ubuntuforums.org/showthread.php?t=282034&highlight=dns](http://ubuntuforums.org/showthread.php?t=282034&highlight=dns)

---

### Post by tighem on 2007-12-10
I use opendns (set on my router) and also have installed dnsmasq, which "caches" dns queries locally. This may help your overall browsing experience.

---

### Post by thered on 2007-12-11
fineas:  I've had FF ipv6 set to disable for some time, doesn't seem to help.  I tried the other points -permanent disable and setting dns to openDNS server again - but the network stops functioning.

tighem: As soon as I set openDNS in my router the network fails, this is no good to me, I like to have full access to my other machines and storage.

Although not a network expert, I can't really see how changing the WAN dns to openDNS **can** affect my LAN  - but it does, perhaps someone can explain that in layman terms.

---

