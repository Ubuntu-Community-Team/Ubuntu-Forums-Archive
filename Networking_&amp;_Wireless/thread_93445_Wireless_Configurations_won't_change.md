---
title: "Wireless Configurations won't change"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by onejoy on 2005-11-22
I just installed Ubuntu on my laptop (I'm new to using Linux).  I was able to install ndiswrapper and can see my wireless card just fine, and it has a 100% singal.  However, it just has a signal that isn't necessarily to my network.

The Essid is off/any and the access point is 00:00:00:00:00:00 however when I got in and use iwconfig to reconfigure my wireless card, none of the changes actually happen.  I've been trying:

```
iwconfig wlan0 essid "holmes" ap 00:07:E9:F5:13:76 channel 10
```

i also tried adding commit to the end of that, as I read in another thread.  It doesn't like channel 10, or freq [frequency] either, and gives me an error with that each time.  when I leave it out, nothing in the wlan0 config changes.

---

