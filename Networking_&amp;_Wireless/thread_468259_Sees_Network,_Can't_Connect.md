---
title: "Sees Network, Can't Connect"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by OrionDartanyu on 2007-06-08
Well I'm new to linux as a whole, and just got my 7.06 Desktop installed, and am quite excited about beginning to learn. So hopefully this hasn't been posted before since the Check If Already Posted doesn't seem to work for me right now, lol.

But anyways, I have the Edimax EW7128G PCI Wireless Adapter (is supported per sticky) and I can see my Wireless network as well as my neighbors. However, when I attempt to connect to mine, it never works. I verified I changed the WEP to 64/128 bit, have typed the WEP key in MANY times, so no typos, and it attempts but then ends up as not connected. I'm almost positive my WEP is Open, however upon venturing into my router, I was unable to confirm this, so just in case I tried Shared... it froze my computer. I rebooted, tried Share once more, again computer froze. So, I figured this might be an encryption situation, so I attempted to connect to my neighbors unencrypted network to verify if it's an encryption issue or not, and same results... it attempts but ends up as not connected.

Now I'm starting to think there is more configuration that needs to be complete, I just figured that since I could see the network, it should be ready to connect. So is it an issue where more configuration is needed, or is it genuinely that I just can't connect?

Thanks very much (in advanced) for the support

---

### Post by upfwnv03 on 2007-06-10
These 3 threads helped me. It was not until I got rid of the Network Manager app. and installed WICD that I made any progress. I still had to do some tweaking, mainly change from WEP to WPA2. Once I did that WICD was able to see and connect to my AP.

[http://ubuntuforums.org/showthread.php?t=469142](http://ubuntuforums.org/showthread.php?t=469142)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

---

