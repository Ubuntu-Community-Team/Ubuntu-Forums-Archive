---
title: "Very slow wireless speeds"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ashwinhgtx on 2010-05-02
My ThinkPad has an Atheros AR5212 wireless card. The connection speeds are too low to be any use for browsing and the link gets dropped every now and then. The connection speed under Connection Information of the Network Manager ranges from 'Unknown' to 2Mbps. The card works flawlessly in Windows and speeds are shown as 54Mbps which is the theoretical maximum for the card.


Can anyone help me fix this? My friend is not able to migrate to Ubuntu because of this problem. Both of us have identical ThinkPads but I have another wired internet connection which I am using now. The wireless is just too slow. Even Google cannot be loaded.

---

### Post by ashwinhgtx on 2010-05-03
Bump.:confused:

---

### Post by ashwinhgtx on 2010-05-07
Bump :(

---

### Post by digital-cipher on 2010-05-15
I have the same problem, can anyone help with this problem

---

### Post by Kafubie on 2010-05-15
I'll bump for you guys.
:(

---

### Post by EthanMN on 2010-05-15
I had this problem last year, I fixed it by making sure that the adapter encryption standards matched what my router is using at that time, for example WPA2 and AES+TKIP. It may take some fiddling.

---

### Post by ashwinhgtx on 2010-05-16
> **EthanMN said:**
> I had this problem last year, I fixed it by making sure that the adapter encryption standards matched what my router is using at that time, for example WPA2 and AES+TKIP. It may take some fiddling.

Do you mind elaborating on how you managed to get it working? :)

---

### Post by JohnDoe365 on 2010-05-19
Sorry guys, it seems the whole 10.04 WiFi system as is has speed issues. There are loads of similar complaints regarding different kinds of hardware.

Please try the follwing, when speed is slow:

disable WiFi
enable WiFi and wait for re-association.

Is speed back to normal? Also see [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3) and [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

Also consider to leave a message at [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936) to raise awareness.

NB: This works only temporal, speed drops back to unaccptably slow after some random time.

---

