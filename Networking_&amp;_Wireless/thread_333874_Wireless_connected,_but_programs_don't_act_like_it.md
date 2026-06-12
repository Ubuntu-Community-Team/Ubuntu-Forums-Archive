---
title: "Wireless connected, but programs don't act like it"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by ithepuertoricanpony on 2007-01-08
UBUNTU 6.06 DAPPER DRAKE
WPA PERSONAL (i believe)

I'm connected to my network through my netgear wg511t. the router is a linksys wrt54g. the wireless network monitor in the system tray displays signal strength, displays my network and a few others in the area. i'm connected to it. however, when i try to go any website with firefox, i get a message saying the server can't be found. i get similar messages no matter what program i use that connects to the internet. i'm pretty sure it's a simple problem. i've had it happen briefly when i connect the actual dsl router to the computer, not the wireless router. wireless works on the other computer in the house, and worked on my laptop when i was running xp.

i'm still new to linux. i just converted to it from windows within the last five days. i'm pretty sure there's a simple setting somewhere i'm not aware of.

](*,)

---

### Post by Crooksey on 2007-01-08
```

dhclient ethX

```

Replace X with interface name.

---

