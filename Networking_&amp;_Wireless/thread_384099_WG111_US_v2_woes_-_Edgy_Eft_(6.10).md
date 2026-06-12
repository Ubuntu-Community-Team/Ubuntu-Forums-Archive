---
title: "WG111 US v2 woes - Edgy Eft (6.10)"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by JohnnyGFX on 2007-03-14
Okay… here is what I have:

Ubuntu Edgy Eft (6.10) with a Netgear USB WG111 US v2 (though which v2 I'm not sure) plugged into it.

Trying to connect it to a Linksys WRT54G v5 router…

I’ve tried all I could think of to get it to connect but I’ve hit the wall on it…

It seems to recognize the wireless Netgear USB card, but it doesn't actually connect to the network.

I've tried a number of different things, but I'm running out of ideas. I heard from a whole bunch of people that Ubuntu has problems with wireless connections and a few cases where it was so frustrating trying to get it to work that people gave up entirely and switched operating systems. I'm about to do that myself if I don't find a solution to get it on the wireless network.

Any help would be greatly appreciated. Please be extra specific if you're going to offer help to me because I'm very much a noob when it comes to Linux and really don't know all that much about it.

---

### Post by n00b@linux on 2007-03-15
Keep the faith.  Nothing worth having comes easy.  I have a WG111T.  To say it was difficult to configure is an understatement - but I got it going and it works perfectly well.  Now let's see if we can get your WG111 v2 working.
 
For starters, we need to know the chipset is uses.  To do this we need to list the devices making use of the Universal Serial Bus, but in 'verbose' mode:```
sudo lsusb -v
```You should see your WG111 listed in detail.  Please post that section (not the whole output as it's very long) to this thread so that we can have a look.
 
Also, you'll need to have the latest version of ndiswrapper installed FROM SOURCE.  Don't use Synaptic to grab the one in the Ubuntu repos as it's broken.  [See my thread]("http://www.ubuntuforums.org/showthread.php?t=333355").

---

