---
title: "Qualcomm Atheros QCA6174 seems to &quot;dislike&quot; AC"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by neroux on 2016-07-27
I have a Qualcomm Atheros QCA6174 adapter with the firmware taken from [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware) and experience connectivity issues with a hidden 5 GHz AC network.

When the network is **initially** added it *usually* manages to connect, but once disconnected (either manually or via a reboot or suspend) it struggles to reconnect. Either it takes up to 2 minutes, while its state is toggling between inactive and scanning or it does not connect at all and mentions a "failed activation".

The interesting part is, it seems to work fine when the same network is made visible, respectively does not seem to have the same issues with a hidden N network on 2.4 GHz.

Anyone an idea what is going on and how it could be fixed?

---

### Post by neroux on 2016-07-28
Nobody any idea?

---

### Post by jeremy31 on 2016-07-28
Does the problem exist when the networks are not hidden?

---

### Post by neroux on 2016-07-28
Thanks Jeremy, please see above. No, when the network is visible it seems to connect fine (still slower than Windows, but still within an acceptable range).

---

### Post by jeremy31 on 2016-07-28
Forgot about that, was searching the ath10k dev's mailing list.  See the wireless script link in my signature and post results

---

