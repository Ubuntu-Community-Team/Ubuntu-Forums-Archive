---
title: "Lubuntu 15.10 don't see the wifi card on HP nf288ea"
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by matteoraggi on 2016-04-27
Compaq Mini  HP nf288ea don't see the wifi card with lubuntu 15.10. how ot patch it?

---

### Post by jeremy31 on 2016-04-27
If you have ethernet connection please open a terminal window and enter ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

And post the contents of the wireless-info.txt file using code tags, use the # in advanced reply

---

