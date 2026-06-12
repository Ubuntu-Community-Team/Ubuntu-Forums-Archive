---
title: "slow internet? 1/10 the speed of windows?"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by onesojourner on 2008-05-04
This problem really has me stumped. I have been using the same wireless card since breezy 5.10 beta. My internet is painfully slow with 8.04. My wireless card is a ralink shipset. Does any one have any idea what would cause this? these tests were done on the same machine connected to the same network. I also connected to the same host to run the test.

xp
[IMG]http://i291.photobucket.com/albums/ll311/onesojourner/windowsspeed.jpg[/IMG]

ubuntu 8.04
[IMG]http://i291.photobucket.com/albums/ll311/onesojourner/Screenshot-1.png[/IMG]

---

### Post by onesojourner on 2008-05-05
this is a bug and its a beast for an lts.

try this:
```
sudo iwconfig wlan0 rate 54M
```

wlan0 is the name of your wireless interface. Yours might be different.

---

### Post by Paris Heng on 2008-05-05
> **onesojourner said:**
> This problem really has me stumped. I have been using the same wireless card since breezy 5.10 beta. My internet is painfully slow with 8.04. My wireless card is a ralink shipset. Does any one have any idea what would cause this? these tests were done on the same machine connected to the same network. I also connected to the same host to run the test.

xp
[IMG]http://i291.photobucket.com/albums/ll311/onesojourner/windowsspeed.jpg[/IMG]

ubuntu 8.04
[IMG]http://i291.photobucket.com/albums/ll311/onesojourner/Screenshot-1.png[/IMG]

Hi, where did you get this beautiful interface? Can PM the links? thnx

---

