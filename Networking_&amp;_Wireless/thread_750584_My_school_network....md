---
title: "My school network..."
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Bluemotion on 2008-04-09
Hi everyone!
i have an odd problem accessing my schools wifi network.
okay so,
at home i have a wireless setup that works flawlessly, in both vista and ubuntu.

but when i goto school vista connects fine to the school network but ubuntu unfortunately cant. i enter the network key, and eventually its just ask me again for it.
is it possible to prevent laptops using OSes other than windows connecting?

hardware/software detail
-using default network manager in 8.04 hardy
-Dell xps m1330
-wireless card intel 4965 agn
-ubuntu hardy heron 8.04

home network is wpa personal and
schools is wep 128bit enc.

I just really cant stand using vista esp. when i have ubuntu installed; its just so slow.:mad:

thanks, BlueMotion.

---

### Post by kutjara on 2008-04-09
> **Bluemotion said:**
> Hi everyone!
i have an odd problem accessing my schools wifi network.
okay so,
at home i have a wireless setup that works flawlessly, in both vista and ubuntu.

but when i goto school vista connects fine to the school network but ubuntu unfortunately cant. i enter the network key, and eventually its just ask me again for it.
is it possible to prevent laptops using OSes other than windows connecting?

hardware/software detail
-using default network manager in 8.04 hardy
-Dell xps m1330
-wireless card intel 4965 agn
-ubuntu hardy heron 8.04

home network is wpa personal and
schools is wep 128bit enc.

I just really cant stand using vista esp. when i have ubuntu installed; its just so slow.:mad:

thanks, BlueMotion.

It's certainly possible for networks to bar certain OSes. I was in a hotel last week with my OS X machine and couldn't connect to the guest network. When I contacted customer support, I was told that they "had to open a special port" to enable access for Mac users. When I pressed the guy for details about this "special port" he got a bit vague and uncertain.

Something similar is certainly doable with Linux, but whether or not your school has implemented such a policy is debatable. Your problem may simply be a result of the way network-manager handles WEP with your particular wifi card. It might be worth doing a search on these forums on the topic of hex vs ascii WEP keys. Some routers are a bit picky about the format they'll accept.

---

