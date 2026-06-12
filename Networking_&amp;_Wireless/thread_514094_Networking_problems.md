---
title: "Networking problems"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by australopithecus on 2007-07-31
I had installed Xubuntu Feisty a few months ago; used it a lot and loved it, and then stopped for a few months.  Meanwhile, I moved and I now have to set up my wireless connection at my new place.

The problem is that I can't seem to find out how to do this!  The help documents that I can find all refer to Applications->System->Networking - but I don't have "Networking" under Applications->System!

I'm sure I should have it somewhere in the installation, since I set it up earlier - just don't know where.  Meanwhile, I have no wired or unwired internet access from this machine.

Any help would be appreciated.  Thanks.

---

### Post by Chappy7777 on 2007-07-31
If I'm wrong on this don't get mad at me, ok. :)

Instead of looking under Applications, you should go to:

System/Administation/Networking (or network). Someone steered you the wrong way, or, I am reading your question wrong, which is quite likely. 

One thing about these forums, you never know if it's the blind leading the blind, or whether the seeing eye-dog is actually awake. :rolleyes:

---

### Post by ugm6hr on 2007-07-31
IN **X**ubuntu7.04 (Feisty) - it should in fact be Applications->System->Network.

If it's not there - you have somehow managed to delete it from the Menu (not sure how).  You can access it by Alt+F2: *gksu network-admin*

However - if you want to get wifi sorted with Xubuntu - I'd recommend Wicd (see my signature below).  It will allow to to configure wired and wireless much easier, and has WPA support (not default in Xubuntu).  Just follow the FAQ for how to install / use.

Before going any further though - check what wifi card you have (look for Ethernet / Network controller):
```
lspci -nn
```

---

### Post by australopithecus on 2007-07-31
Thanks for both replies.

I must have indeed somehow managed to delete "Network" from Applications->System.  Any idea how I can get it back there?

Finally, gksu network-admin does nothing at all; just returns me to the command line.  No new windows, etc.

---

### Post by ugm6hr on 2007-07-31
> **australopithecus said:**
> Thanks for both replies.

I must have indeed somehow managed to delete "Network" from Applications->System.  Any idea how I can get it back there?

Finally, gksu network-admin does nothing at all; just returns me to the command line.  No new windows, etc.

Hmmmm...

I would suggest trying Wicd if you are going to have to download something (see my signature below).

If /usr/bin/network-admin doesn't exist, then I'm not sure where you've put it.  I suspect you can download it - but you may as well use Wicd.

---

