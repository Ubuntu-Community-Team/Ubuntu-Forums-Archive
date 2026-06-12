---
title: "Question on compatibility of TL-WN821N V5 with Ubuntu"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by zzz... on 2018-09-20
Hey I'm quite new and before I jump into Ubuntu I want to understand what I'm getting myself into and that means knowing if my drivers are fully compatible and if not what measures do I need to take to make sure it is. I researched extensively for an fix/answer and found one but it seemed to be from a year ago etc so I'm not sure if it would be outdated by newer 'patches'.

Network Driver: TL-WN821N V5 

Driver Page: [https://www.tp-link.com/us/download/TL-WN821N_V5.html](https://www.tp-link.com/us/download/TL-WN821N_V5.html)

Thread: [https://ubuntuforums.org/showthread.php?t=2351228](https://ubuntuforums.org/showthread.php?t=2351228) (Apparently this was a fix)

Also curious if there is any difference if I installed Elementary OS (Would the same fix work?)

---

### Post by zzz... on 2018-09-20
also how would I go about doing this without an internet connection? I can get the github files from my other pc but what about the DKMS stuff.

---

### Post by jeremy31 on 2018-09-20
That device is supported in kernel 4.15 that is used in Ubuntu 18.04
I don't know about EOS

---

### Post by zzz... on 2018-09-20
> **jeremy31 said:**
> That device is supported in kernel 4.15 that is used in Ubuntu 18.04
I don't know about EOS

Yep. Just switched to Elementary OS and it's working out of the box. Thanks. May I ask how you knew it worked out of the box? I am genuinely curious

---

### Post by jeremy31 on 2018-09-20
The thread with the fix showed Bus 003 Device 009: ID 2357:0107 and I know that is a TP-Link wifi device and I just did a terminal command on Ubuntu 18.04
```
modprobe -c | grep 2357 | grep 0107
```
It showed that that device would use the kernel module rtl8xxxu

---

