---
title: "Kernel panic when connecting to wireless network"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by janlugt on 2007-10-21
I have an (somewhat faulty) Acer Aspire 1300 without wireless support built-in, so I added a Linksys WPC11 (Realtek R8180L chipset) for wireless support. The optical drive is broken on this notebook, so I had to install Ubuntu using a desktop PC and a IDE-to-USB-adapter, which has worked out fine.

I encounter problems when connecting to a wireless network. As soon as I connect to my home network, fill in the WEP-HEX-string and choose to connect, the kernel panics and I get a unresponsive system with a blinking scroll-lock and caps-lock.

How can I use my wireless card without kernel panic?

---

### Post by janlugt on 2007-10-21
Solved by reverting to Ndiswrapper + NET8180-drivers from the realtek-website. Works like a charm.

---

### Post by stillerz on 2007-10-28
Hi,

I'm having this same problem with a WPC11 v4 card on my Thinkpad T22, but when I followed the steps to install ndiswrapper and the drivers from the realtek site, I'm still getting the problem - freezes and locks the whole system after I enter the WEP key.

I even tried adding these blacklist entries (/etc/modprobe.d/blacklist):
blacklist r818x
blacklist ieee80211_rtl
blacklist rtl8180

But, same results.

Can you show the link for the exact drivers you downloaded from realtek and any special steps you used to disable the drivers that come with Gutsy for this card?

Thanks!

---

### Post by willingc on 2007-10-30
Try looking at Rzulf's response to a similar question on the T21.  Good luck.

[http://ubuntuforums.org/showthread.php?t=584046&highlight=t21]("http://ubuntuforums.org/showthread.php?t=584046&highlight=t21")

---

