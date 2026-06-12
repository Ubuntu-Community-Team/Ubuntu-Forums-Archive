---
title: "No Internet"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by robman9000 on 2007-10-01
I've been on Ubuntu 7.04 for a while now and it's worked beautifully. Unfortunately, the other day, my roommate plugged his Wii Access Point dongle into a USB port on my computer and the internet's been wonky ever since. And by wonky, I mean it just doesn't work. Last night I was able to fiddle with the settings somehow to get it to work, but I'm not 100% what I did, and this morning when I started it up, the Internet wasn't working again. I'm pretty sure the Wii dongle is responsible for this error, but I haven't seen anyone else report the same problem.

Any help would be much appreciated. Thanks.

---

### Post by robman9000 on 2007-10-01
Update:

It seems that changing my settings by switching to a Static IP seems to have fixed the problem. I think there may have been a problem where the computer couldn't find the proper gateway address or something like that.

---

### Post by cameronjcc on 2007-10-01
First of all:  Tell you roomate to stop put his Dongle in your Port.  That's just not good roommate etiquette.
:lolflag:


Sorry, just couldn't let that one pass me bye.


But really, have you checked your 

sudo gedit /etc/network/interfaces

To make sure there aren't any improperly listed interfaces there?

---

