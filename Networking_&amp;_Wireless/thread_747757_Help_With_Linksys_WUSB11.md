---
title: "Help With Linksys WUSB11"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by KanakhaJ on 2008-04-06
I've been trying to get my Xubuntu pc connected to my wireless network with my WUSB11v2.5 all day. I've about had it with trying to fix something that just won't fix. I've followed all of the instructions on this page: [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11?highlight=%28WUSB11%29](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11?highlight=%28WUSB11%29) even when errors in the terminal came up saying that "CVS could not be found". What do I have to do to get on the internet with my pc???:confused:

---

### Post by KanakhaJ on 2008-04-07
Anyone? I really need help with this.

---

### Post by wieman01 on 2008-04-07
You could get it to work using my Ralink tutorial (see signature). If you have problems, I'll guide you through it. I think that's the shortest route for you.

---

### Post by KanakhaJ on 2008-04-07
I'm not so sure a Ralink tutorial will help with a Linksys problem...:(

---

### Post by wieman01 on 2008-04-08
It does not matter, my Ralink tutorial is universal. :-) In fact my Linksys WUSB54G V4 has a Ralink chipset. Please take a look at the tutorial and give it a go. Trust me. :-)

---

### Post by adisor19 on 2008-05-08
> **wieman01 said:**
> It does not matter, my Ralink tutorial is universal. :-) In fact my Linksys WUSB54G V4 has a Ralink chipset. Please take a look at the tutorial and give it a go. Trust me. :-)

But, the WUSB11 v2.5 is NOT Ralink bsed. It's a PRISM 2 chipset so your tutorial doesn't apply. :(

And yes, i'm in the same boat as the original poster.

Adi

---

### Post by wieman01 on 2008-05-08
It still applies because my approach is a rather generic one. "ndiswrapper" lets you install basically any wireless device.

---

### Post by adisor19 on 2008-05-10
> **wieman01 said:**
> It still applies because my approach is a rather generic one. "ndiswrapper" lets you install basically any wireless device.

Fair enough. Wifi will probably work this way. However packet injection is a no go do to not using the proper Prism2 drivers :(

Adi

---

### Post by wieman01 on 2008-05-11
Well, the OP wasn't in any way asking for packet injection, so...

---

