---
title: "[SOLVED] Cannot connect to Wikipedia"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by sci-fi guy on 2008-03-07
My system is having some issues with Wikipedia. I get "Page Load" errors and "Network Timed out". This is occurring both at school and from home, and other systems on the same connections do not seem to be affected. Using the IP address takes me to a "Wiki does not exist" page on WikiMedia. I had Wikipedia in my hosts file at one point, but I removed it some time ago. Currently I am using Firefox 3 beta 3 on Hardy Heron (upgraded from Gutsy, not reformatted) but I was having this problem before the upgrade. This could be related to me trying to give my eth0 connection a second IP address, but I do not see how. After all, the rest of the Web seems to work fine.

---

### Post by Paris Heng on 2008-03-07
> **sci-fi guy said:**
> My system is having some issues with Wikipedia. I get "Page Load" errors and "Network Timed out". This is occurring both at school and from home, and other systems on the same connections do not seem to be affected. Using the IP address takes me to a "Wiki does not exist" page on WikiMedia. I had Wikipedia in my hosts file at one point, but I removed it some time ago. Currently I am using Firefox 3 beta 3 on Hardy Heron (upgraded from Gutsy, not reformatted) but I was having this problem before the upgrade. This could be related to me trying to give my eth0 connection a second IP address, but I do not see how. After all, the rest of the Web seems to work fine.

I also having the same problem, please somebody assist.

---

### Post by lsmobrian on 2008-03-07
That is a weird problem, these are just a few things off the top of my head, dont know if any will fix the problem maybe just narrow it down


I get the same thing using the IP 208.80.152.2, so nothing wrong with that  (On a mac now)

can you ping or trace route wikipedia, maybe check ip routing table?   

```
ping www.wikipedia.org
traceroute www.wikipedia.org
route get www.wikipedia.org
```


Maybe try a different browser to see if its firefox
```
sudo apt-get install lynx
lynx www.wikipedia.org
```

Also might look at
[ubuntu wiki, connected but no internet]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2")


If its firefox, try going into offline mode and then back to normal, see if that helps, maybe ff saved incorrect dns info

---

### Post by sci-fi guy on 2008-03-07
> **lsmobrian said:**
> can you ping or trace route wikipedia, maybe check ip routing table?
Yes.
> **lsmobrian said:**
> Maybe try a different browser to see if its firefox
Got wikipedia's front page (the language selection hub) but couldn't navigate further. I've also gotten the front page once or twice in FF.
> **lsmobrian said:**
> 
Also might look at
[ubuntu wiki, connected but no internet]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2")
Not helping.

> **lsmobrian said:**
> If its firefox, try going into offline mode and then back to normal, see if that helps, maybe ff saved incorrect dns info
Nope. *sigh*

---

