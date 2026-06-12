---
title: "Ubuntu has extremely slow servers"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by faraz_k86 on 2010-04-13
till 8.10 anything i downloaded from the synaptics manager would download at my maximum speed of around 90 - 100 kbps..

but now anything i download from the ubuntu software center downloads at 5kbps or at most 15kbps..

i even tried changing servers from my country server to main ubuntu server but it was of no use.. still the same speed..

am I the only one experiencing this? could this be a fault in my wifi driver?

---

### Post by Silent Warrior on 2010-04-13
Well, I can tell you that doesn't happen to me at all. Generally. I share the connection, however, and sometimes it just isn't possible for me to use the internet at all - occasionally I can't even check my e-mail. If you're in a similar situation, that would explain it. Do you always update at the same time of day? (Then you could try a few hours earlier or later?)

---

### Post by egalvan on 2010-04-13
> **faraz_k86 said:**
> ...i even tried** changing servers from my country server to main ubuntu server** but it was of no use.. still the same speed..

am I the only one experiencing this? could this be a fault in my wifi driver?

If you are using different servers, and still seeing the same low speeds, then yes, it is on your end of the line...

And as of an hour ago, my updates ran at approx 100KBs...

So again, yes, it's at your end.

---

### Post by lisati on 2010-04-13
Have you tried the "select best server" option?

---

### Post by Drenriza on 2010-04-13
i just downloaded with 800-900kbps

---

### Post by f1r3flie on 2010-04-13
Check to see if it's faster on servers closer to your home, if only slightly. If the speed varies by distance from you, the bottleneck's probably on your ISP's end. If it's the same for all, it's most likely either your router or WiFi.

---

### Post by PenguinInside on 2010-04-13
> **faraz_k86 said:**
> till 8.10 anything i downloaded from the synaptics manager would download at my maximum speed of around 90 - 100 kbps..

but now anything i download from the ubuntu software center downloads at 5kbps or at most 15kbps..


Hmm, you can specify which servers you want to use.

Also, and this doesn't directly apply, but the Ubuntu CD image download servers are very slow for me, so I generally download via BitTorrent.

---

### Post by airtonix on 2010-04-13
kbps = kilobits per second.
kb/s kilobytes per second.

100 kbps = 10 kb/s
I use the ubuntu mirror provided by my ISP, so i get updates at around 1.2mb/s

original poster needs to confirm that downloading files from anywhere at all gains speeds above the described 1.5kb/s

try downloading this : 
[http://mirror.internode.on.net/pub/test/100meg.test](http://mirror.internode.on.net/pub/test/100meg.test)

What kind of  speeds do you get while downloading that?

if your computer is a laptop, pick it up and walk around the home with it... do the speeds change drastically ? 

Its my assumption your wifi reception has become quite poor for some reason.

I would make yourself a [cantenna]("http://www.turnpoint.net/wireless/cantennahowto.html"), connect it to your wifi card and point it at your wifi access point.

---

### Post by faraz_k86 on 2010-04-13
Its not my connection.. I dont share it with anyone and I alone use the DSL line, also the same connection works at maximum speed in my windows installation.. its just the ubuntu software center and update manager that are extremely slow..

I have also tried closing my own country server and than main server.. no difference..

> **airtonix said:**
> kbps = kilobits per second.
kb/s kilobytes per second.

100 kbps = 10 kb/s
I use the ubuntu mirror provided by my ISP, so i get updates at around 1.2mb/s

original poster needs to confirm that downloading files from anywhere at all gains speeds above the described 1.5kb/s

try downloading this : 
[http://mirror.internode.on.net/pub/test/100meg.test](http://mirror.internode.on.net/pub/test/100meg.test)

What kind of  speeds do you get while downloading that?

if your computer is a laptop, pick it up and walk around the home with it... do the speeds change drastically ? 

Its my assumption your wifi reception has become quite poor for some reason.

I would make yourself a [cantenna]("http://www.turnpoint.net/wireless/cantennahowto.html"), connect it to your wifi card and point it at your wifi access point.


thankd for the links.. I downloaded the test file and it downloads at 126 KB/sec

---

### Post by sandyd on 2010-04-13
try using apt-p2p and see if its faster

---

