---
title: "Wireless Intel 3945ABG Problems"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by airmind on 2007-01-14
I have a Gateway MX6955 laptop which comes with an Intel 3945ABG wireless card. I tried setting it up, but I just couldn't connect it. I`m using Edgy by the way.
I set all the correct information on the Networking program, but it doesn't show me any information if it is connected or not, but I cant connect to the internet. In ifconfig it is recognized as eth1 and it says it is an Ethernet connection. Shouldn't it be wlan0?
I installed network manager and it doesn't show in the list, all it shows is Wired Connection.

And my wireless connection is working because it works on Windows XP on the same laptop, and in another one.
Could ndiswrapper help me?
Oh, and I`m using WPA with a shared passkey, and WPASupplicant is installed (edgy`s default?).

Thanks a lot.

---

### Post by airmind on 2007-01-14
I finally got it working. It turns out I had to disable all my networks in Ubuntu so that Network Manager was able to recognize them. And so far, Network Manager is REALLY great. WPA is working fine as is everything else. 
There should be some kind of sticky with instructions for it.

Oh, and by the way, this fixed a problem where Ubuntu would stop at boot waiting for DHCP. I took a long time to discover what was the problem, and now that I disabled all my networks in Ubuntu, it is booting much faster.

---

