---
title: "housesitting means wireless network woes"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by igeterrors on 2007-03-30
Hi all, 

A couple times a year I housesit for some friends who use Macs and they have the wireless Airport thingy and the little base stations around the house.  Generally after about 3 days of really random tweaking I'm able to finally get a connection.  But I'm over here again for 10 days and I can't go through that again!

So the situation is, when I do a iwlist scan I can see the network, the essid, the mac address, everything.  And since I have been connected here before with the same hardware, I know it's possible.  It's just that when I finally did it, it was so random and came after days of trying anything at all, that I really have no idea of wht ai did that worked.  Every time I try to do a ```
sudo iwconfig eth1 essid mynetwork
``` it doesn't seem to have any effect.  It still shows essid: "any/all".  Also if I try setting the access point, there is no change afterward either.  It just says "no association."

Also, it takes me about a day and a half to get back on my wireless network at home after I'm finished housesitting.  There's got to be a better way!

From other posts I've read, it seems that from where I am now I'm pretty close.  But what's the final step?

:popcorn:  anyone who helps: the popcorn's on me!

---

### Post by josephus on 2007-03-31
Is WEP enabled?

---

### Post by igeterrors on 2007-03-31
WEP is not enabled, but thank you for your reply.

I can report what the solution was -- I'm not even sure what prompted me to try it; but like my post said, lacking any actual knowledge, I just try all kinds of random things.

I went into my .bashrc file and added the lines:

```

sudo iwconfig eth1 essid mynetwork
sudo iwconfig eth1 ap 00:11:22:33:44:AA
sudo dhclient

```

Then logged out and logged back in again.  Bingo.  Weirdly, I had tried these exact commands from the command line and they did nothing.  I even tried it as root and it did nothing. But adding them to my .bashrc did the trick.  Hopefully this will help someone else.

---

