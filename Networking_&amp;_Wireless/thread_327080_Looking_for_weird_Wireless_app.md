---
title: "Looking for weird Wireless app"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by cody_04l on 2006-12-28
Hey guys,

Im not sure if this is possible but I was looking for an application that would show you where a wireless ap is in respect to your current location.

Like it would have a simple map/graph/ and show you that ssid "freewireless" is 15ft north west. Ssid "tmobile" is 25ft southwest.

Anyone know of anything like that?

thanks.

---

### Post by Floppyjoe on 2006-12-28
SWScanner works with a GPS Device to find locations but you need a GPS device to use it for finding locations. These go for about $150 Canadian Dollars in my neck of the woods. It does however find AP's that are around your location.

---

### Post by tturrisi on 2006-12-28
Kismet will do that if have a gps device, they cost about 75 bucks here in US, like the one that comes with MS Streets & Trips.

---

### Post by cody_04l on 2006-12-28
Hey guys thanks for the suggestions. I was aware you could do it with GPS. I was more looking for something that uses the wireless card and displays the ap's that it finds right that second. Only the networks that the wireless card finds. And maybe displays in a little map or something that gives distances.

Im not sure if a wireless card is capable of determining distances likes that.

---

### Post by tturrisi on 2006-12-29
> **cody_04l said:**
> Hey guys thanks for the suggestions. I was aware you could do it with GPS. I was more looking for something that uses the wireless card and displays the ap's that it finds right that second. Only the networks that the wireless card finds. And maybe displays in a little map or something that gives distances.

Im not sure if a wireless card is capable of determining distances likes that.
In order to determine distances, you need 3 points of reference: the location of the adapter, the location of the AP and a third reference point used to triangulate (satellite or loran).  This is basic geometry.  An adapter cannot do this alone because 80211 protocol does not broadcast locations because it has no way of determining its location to begin with.

Even if an application contained a database of known AP locations, such as recorded wifi hotspots, and also contained a database of all possible lattitude-longitude points, the application would still need GPS to determine the AP location and then do distance calculations.

---

