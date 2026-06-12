---
title: "Network storage wreaking havoc on my system"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by thegodfaza on 2008-07-13
I recently switched from Fedora to Ubuntu since Fedora doesn't support my wireless configuration and I heard Ubuntu does. I have everything working except for a few things.

1) When I attempt to sleep or hibernate the system hangs and I get:
```
[  140.04720] EIP: [<f8aa4e7e>] ieee 80211_virtfs_vdetach+0x8e/0xf0 [wlan] SS:ESP 0068:f3edde64
[  140.047144] ---[ end trace 1071aab4018ab1d7 ]---
```
Now this started happening when I put my network storage drives into fstab(I have to do it that way because it is password protected). And it also looks to be related since it refers to 802.11 and wlan.

2) When I attempt to shutdown the system hangs and I get:
```
no response for cmd 50 mid 71
```
This also started happening with my network storage bla bla bla...

I tried turning off my wireless card from the UI and flipping the switch on the card itself. It had the same effect.(btw my computer is a laptop)

---

### Post by thegodfaza on 2008-07-14
I commented out all the lines for the server in fstab and I still have the errors. So anyone have an idea.

---

### Post by thegodfaza on 2008-07-14
Bump

---

