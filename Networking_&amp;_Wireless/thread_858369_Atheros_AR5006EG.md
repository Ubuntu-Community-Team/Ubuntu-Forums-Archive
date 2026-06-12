---
title: "Atheros AR5006EG"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by stephen0731 on 2008-07-13
Hi, I've just installed Ubuntu 8.04. I have an HP Pavillion DV6810us with an Atheros AR5006EG wireless card. The restricted driver seems to be enabled (according to a popup when I start the OS) yet, I can't seem to find anywhere to configure it or locate the wireless network. What am I doing wrong? I'd love to get this working.

---

### Post by chalewa on 2008-07-13
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

### Post by stephen0731 on 2008-07-13
I followed these directions exactly, and still have no functionality from my wireless card. Could it be because I have a 5006EG and not 5007? no wireless networks are being detected in wicd, and as far as I can tell the wireless card isn't functioning. I've tried it with the on/off switch in both positions and it doesn't seem to make any difference.

---

### Post by chalewa on 2008-07-14
try to do a hard shut down of the computer, and then boot it back up. 

can you post ```
ifconfig
```

---

### Post by nickdbliss on 2008-07-14
Post the output of lspci, ifconfig, iwlist scan.

---

