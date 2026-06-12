---
title: "Wifi keeps losing connection &amp; signal is only 33%"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by roadrash on 2007-09-25
I am having problems with Ubuntu fiesty & my Fujitsu Siemens Amilo Li 1718 laptop.

I have everything working on the laptop now including the wifi network using the win xp driver and ndiswrapper.

The problem is with Ubuntu fiesty I get a significantly lower connection signal level than it gets with windows vista and i keep getting random disconections.
Operating the laptop from the same area I get the signal meter in windows showing full (excellent) and in Ubuntu the signal meter shows 2 bars (33%).
My router is a linksys WRT54G and i am using wpa personal encryption - TKIP

can anyone help me to get this working reliably.

---

### Post by MysticEdge on 2007-09-25
Wish I could help mate, I'm having similar problems with the low connection rate.

However, if I had to guess, I would say that the drivers on linux for your wireless card are not matching up exactly. And therefore it's not letting it load properly, at least, that's what I'm going to try.

---

### Post by roadrash on 2007-09-25
I was using it a little while ago and the signal was at 65% but did dip every so often.  Its still not as stable as it is in vista.  The driver that is used is a xp 32 bit driver not the vista one because ubuntu is for 32 bit.
Is there anyone that can help improve this situation?

---

### Post by wastedfluid on 2007-09-25
I thought ndiswrapper supports Windows drivers directly?

Have you tried moving your Windows driver, and having ndiswrapper load it?  Any errors?

---

### Post by robnz on 2007-09-25
What type of adapter is in this laptop?

---

### Post by roadrash on 2007-09-26
> Have you tried moving your Windows driver, and having ndiswrapper load it? Any errors?

yes and no errors.

> What type of adapter is in this laptop

Its a Atheros AR5007EG (rev01)

I read somewhere that knetwork can be resposible for the disconnections.  Is this correct and if so where do i enter my wifi settings so knetwork could be removed.
I cant think what could make the signal lower than it is in windows though.

---

### Post by robnz on 2007-09-29
I had a similar problem. Low reported signal strength and frequent disconnects leading eventually to complete wifi failure. Turned out to be a background scanning problem.

[Check this post.]("http://ubuntuforums.org/showpost.php?p=3421545&postcount=4")

Now my wifi performance is excellent. The signal is still reported low but transfer speeds are fine.

Rob

BTW: I'm using the built in ath_pci module not ndiswrapper.

---

