---
title: "help me with bcm4318 [Air force one 54g] 802.11g wireless"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by jaoak1978 on 2008-11-12
hi all of you lucky linux users out there I am having problems getting my wireless card to work I have tried for three days to get it to work I am at my witts end I cannot get it I really want to switch to linux and stop using windows all together cause I really like it I have a think pad t40 and i downloaded the version of ubuntu from wubi please somone give me a step by step I have tried to do this for four days I know I am close but I think I need a fresh start thanks to anyone who can help:)

---

### Post by Sealbhach on 2008-11-12
Look for the driver in System/Administration/Hardware Drivers.

If that doesn't work, try these commands here:

```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart

```

Ref: [http://ubuntuforums.org/showpost.php?p=6131819&postcount=5](http://ubuntuforums.org/showpost.php?p=6131819&postcount=5)


.

---

