---
title: "[SOLVED] Unable to connect to internet, wired or wireless"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by crisnoh on 2008-02-10
Hey everyone, I've been running 7.10 for a while now and this problem just cropped up.

I've been using the internet (both wired and wireless) on my system for almost a year, upgraded to 7.10 about 2 months ago with no problems until a couple days ago.  I just switched internet providers and all of a sudden I can't connect to the internet via an ethernet cable.  Haven't tried a wireless connection yet because the router hasn't been set up.  My wifes Windows system, from which I am currently writing this post has no problems connecting.  However, my brother-in-laws Windows computer doesn't recognize the connection.

Correction, our computers recognize that there is a network that they're plugged into, the just can't access it.  Manually plugging in IP addresses and all that doesn't work either.

If more information is needed let me know.  I'd really like to get this figured out.  Thanks in advance.

---

### Post by Richardinho on 2008-02-10
As you've probably noticed this is one of the most asked question about Ubuntu!
I had this problem myself. The annoying thing is that all the books tell you about how easy it is to connect to the internet using ubuntu so when something goes wrong, it's hard to work out what the problem is.

In my own case I have a dual boot with windows and I could connect my windows partition no bother using my adsl router, but not Ubuntu.
Eventually I updated the driver for my router and since then it's worked perfectly.

---

### Post by crisnoh on 2008-02-11
Well, I'm not actually using a router at the moment.  We're using the internet by plugging directly into the modem.

---

### Post by Iowan on 2008-02-11
Some systems reportedly lock onto the MAC address.  It's possible that resetting the modem (every time) will temporarily help.  Once the router is in place, the modem should see only that MAC and be happy.

---

### Post by crisnoh on 2008-02-11
Yep, resetting the modem did the trick.  I'll keep my fingers crossed for my router setup.

---

