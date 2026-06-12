---
title: "Wireless hook-up"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Javelin Dan on 2009-12-04
I recently bought a Compaq (HP) notebook that had Windows 7 (starter edition) with wireless capabilities. It worked great with my existing wireless network. I then installed Xubuntu 9.08 and everything was fine except no wireless net detected. I hooked into my DSL cable (instant internet) and a pop-up told me 9.10 was available. I downloaded and installed. After restart, I think there were several networks detected (icons to right showed signal strength - my neighbors?), but after entering ID & password, I couldn't connect. I then clicked on "connect to hidden network" and did the same, but no dice. I'm now out of bullets - please help! Please be as specific and fundamental as possible as electronically, I'm still dragging my knuckles on the ground. Thanks.

---

### Post by jbrown96 on 2009-12-04
What kind of wireless card is it? ```
lspci | grep Network
```

What does ```
iwlist scan
``` report. When you tried to connect to your network, was the encryption type (wep, wpa, wpa2) selected correctly?

---

### Post by Terl on 2009-12-04
> **Javelin Dan said:**
> I recently bought a Compaq (HP) notebook that had Windows 7 (starter edition) with wireless capabilities. It worked great with my existing wireless network. I then installed Xubuntu 9.08 and everything was fine except no wireless net detected. I hooked into my DSL cable (instant internet) and a pop-up told me 9.10 was available. I downloaded and installed. After restart, I think there were several networks detected (icons to right showed signal strength - my neighbors?), but after entering ID & password, I couldn't connect. I then clicked on "connect to hidden network" and did the same, but no dice. I'm now out of bullets - please help! Please be as specific and fundamental as possible as electronically, I'm still dragging my knuckles on the ground. Thanks.

It isn't quite clear to me; when you say you saw the networks listed to connect to, is your own on the list?  If so, are you using wep or wpa?

---

### Post by Javelin Dan on 2009-12-04
Non of the I.D. info shown for the nets detected matches any of the info I recorded for my own.

---

