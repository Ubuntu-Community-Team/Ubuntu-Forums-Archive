---
title: "RTL-8185 Wirless Card Gateway ML3109 Laptop"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by ethanklein on 2008-06-30
I recently just found this link

[http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy]("http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy")

looking around for a better driver for my wifi adapter. If you have experienced extremely weak perfromance with this adapter. This guided w alk through on how to build (posibly the best driver for this adapter) is very handy. I know have 85% average signal about 100 ft from my router.

Cheers Will!

(I take no credit for this driver all credit goes respectably to Will Daniels)

---

### Post by ethanklein on 2008-06-30
I just got home from vacation and I am currently on the internet at least 600ft from my router. How this is possible I dont know. This SHOULD NOT WORK. THY DOES IT?!? This driver is a beast.

---

### Post by wdaniels on 2008-07-02
> **ethanklein said:**
> (I take no credit for this driver all credit goes respectably to Will Daniels)

Whilst I appreciate the sentiment, I need to make clear that I did not write this driver. All I did was patch it for the changes in the 2.6.24 kernel. I believe the original author is a guy named Andrea Merello, although there have been numerous contributors over time (see the changes file).

In all fairness, the real credit goes to Realtek for an excellent chipset. It amazes me that this chipset is typically only used in budget cards yet I find it to be technically well-spec'd and probably the best performing card I own.

Note also that there is a mac80211 port of this driver in the mainline kernel now, which is on it's way to Hardy (see new guide [here]("http://willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy")). The main practical advantage of the newer version is that it supports WPA through NetworkManager (i.e. WEXT) now.

Anyway, glad that you're happy with your card :)

---

