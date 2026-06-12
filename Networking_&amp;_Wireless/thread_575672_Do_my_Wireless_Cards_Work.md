---
title: "Do my Wireless Cards Work?"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by s3a on 2007-10-14
My main goal is to transmit my dial-up connection wirelessly to my laptop. As you can see at: [http://ohioloco.ubuntuforums.org/showthread.php?t=569344&highlight=transmit](http://ohioloco.ubuntuforums.org/showthread.php?t=569344&highlight=transmit)

Now all I need to know is if my wireless cards work out of the box or not. If the cards can scan and detect a wireless signal does that mean they will work? Or is that just irrelevant? If my cards are supposed to work, can someone help me on that other thread, if they need some tweaks, NDISWRAPPER stuff, etc then can someone please help me with that?

Thanks in advance!

---

### Post by kevdog on 2007-10-14
You will need a card capable of being in MASTER mode, which means it can act as an access point.  I know some older orinoco cards can do this, but I believe any atheros based card that is supported by the madwifi drivers can also do this.  ndiswrapper can not do this.  I havent done this personally but it looks like going to the madwifi site to find a model of card you could buy would be the easiest way.

---

### Post by s3a on 2007-10-15
How do I check if my card can act as an access point (MASTER mode)?

---

