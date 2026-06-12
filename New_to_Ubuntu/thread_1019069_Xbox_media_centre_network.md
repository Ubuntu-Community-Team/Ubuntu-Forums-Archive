---
title: "Xbox media centre network"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by SirMikeyB on 2008-12-22
Hello all

I'm having some trouble. I have an old xbox which i have installed XBMC on. Its networked, connects to the interweb and streams music from my computer. When i come to stream video, with a 15mb cache, it lags up after 30 seconds or so.

How can i best rectify this? Could it have anything to do with the fact that my computer with all the videos on is on the other side of the house with a 'fair' connection to the router, according to windows network centre? Does the degridation of the signal between PC and router affect the streaming of video on the xbox?

The xbox is hooked up to a tv in the next room to the router. All of this is wireless. The router supports 802.11g, the computer has a belkin USB wireless G adapter but the xbox is using a net gear wireless bridge system where one 802.11b access point is plugged into the router and the other 802.11b access point is in the xbox.

It works.... just not very well for videos. Im willing to throw some money at it but i dont know wehther to get a better router, a better wireless adapter/card for my PC or what.

Any help would be much appreciated

---

### Post by jimmy the saint on 2008-12-22
The XBOX has very little RAM and a very slow processor so it is best to use a file format that is easy for it to decode.  Try using a different file format and see if that helps.  Remember, the XBOX is close to 9 years old and was not really state of the art hardware even at that time.

---

### Post by anjilslaire on 2008-12-22
I have XBMC on an xbox also, and I stream all my media from my linux sytem as well, only wired.

With the xbox on wireless, and using 802.11b  make sure the router is set to "Mixed Mode" allowing b & g together. Also, I recommend temporarily wiring the xbox to the router to see where the bottleneck is, my guess is the wireless on the xbox side.

Also, make sure all NICs are set to full duplex.

---

### Post by anjilslaire on 2008-12-22
> **jimmy the saint said:**
> The XBOX has very little RAM and a very slow processor so it is best to use a file format that is easy for it to decode.  Try using a different file format and see if that helps.  Remember, the XBOX is close to 9 years old and was not really state of the art hardware even at that time.

The xbox can stream avi & mpeg just fine, as well as flash from youtube. It's likely not a cpu/ram issue.

---

### Post by SirMikeyB on 2008-12-23
would turning mixed mode on help? the router has a wire going to the 1st access point, which sends out the signal to the other access point which is then wired to the xbox.

it sounds as though video streaming over wireless is just not meant to happen at home yet!

---

### Post by Sarmacid on 2008-12-23
> **anjilslaire said:**
> I have XBMC on an xbox also, and I stream all my media from my linux sytem as well, only wired.
I have this set up as well and works perfect, so it must be a wireless issue.

---

### Post by anjilslaire on 2008-12-23
> **SirMikeyB said:**
> would turning mixed mode on help? the router has a wire going to the 1st access point, which sends out the signal to the other access point which is then wired to the xbox.

it sounds as though video streaming over wireless is just not meant to happen at home yet!

You *need* mixed mode to function properly. You have one wireless on G and the other on B, hence your mixed wireless environment.

---

