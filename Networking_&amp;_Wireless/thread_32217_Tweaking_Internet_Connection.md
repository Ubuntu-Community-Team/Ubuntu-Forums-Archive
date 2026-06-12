---
title: "Tweaking Internet Connection"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by richard1985 on 2005-05-06
I find my internet connection is kind of slow with Ubuntu, is there any way to tweak the connection to speed it up?

tia

---

### Post by enquiry on 2005-05-06
What kind of connection is it?

---

### Post by richard1985 on 2005-05-07
The connection type is dsl, though it is going through a router.

Through eMule it gives me an error :

Warning DonkeyServer No1 (xxx.xxx.xx.x:xxxx) - You have a lowid. Please review your network config and/or your settings.

Not sure if that helps any. Also unaware of how to tweak network config and settings. 

(obviously a n00b who appreciates your help, tia)

---

### Post by enquiry on 2005-05-07
How's the speed with non-p2p services? Is accessing web pages also slow? This possibly doesn't have anything to do with Ubuntu, but might just be a firewall setting in your router, or the router might not handle trafic with multiple connections.

---

### Post by derrick1985 on 2005-05-08
I'm a friend of his, and set up his PC, and i'll explain this a bit more:

His computer is up stairs, and he connects through a POS router downstairs. Normally, DHCP finds this IP address, but for some reason, Ubuntu won't (it might be the fact that the internet cable is round 50ft long) so I had to use STATIC settings to get everything set up. And it works. Problem being, the internet speed is slower than his regular windows speeds. Most of the time, it only goes around 150kb/s on High speed cable.

Basically, is there anyway he can try and increase the performance of his downloads?

---

### Post by [pl]ice on 2005-05-09
i don't know about the rest, but this:
Warning DonkeyServer No1 (xxx.xxx.xx.xxxx) - You have a lowid. Please review your network config and/or your settings.

is just you don't have port re-direction on your router, therefore lowID, it's in the options which port to re-direct.... works fine with me.

---

