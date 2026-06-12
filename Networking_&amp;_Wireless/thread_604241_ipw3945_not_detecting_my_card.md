---
title: "ipw3945 not detecting my card"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Elrohir on 2007-11-05
ipw3945 can't detect my Intel PRO 2200BG card? any configuration I must change? or is it the driver?

please, help! :(

---

### Post by kevdog on 2007-11-05
I dont know a lot about intel cards, but would the ipw2200 driver support your card?

---

### Post by Elrohir on 2007-11-06
yes ipw2200 does support my card, but it doesn't come by default... anywhere I can get it? and how do I install it?

---

### Post by Elrohir on 2007-11-06
anybody?

---

### Post by kevdog on 2007-11-06
I thought the driver was in the kernel already.

Can you do the following:

sudo updatedb
locate ipw

See what it shows.  If not 2200 driver comes up, I found this:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

