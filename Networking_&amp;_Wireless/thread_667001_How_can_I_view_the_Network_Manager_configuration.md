---
title: "How can I view the Network Manager configuration?"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by le_jawa on 2008-01-13
I've fouled up my NM config and need to clean it up.  I had my wireless network (hidden SSID, WPA, etc) configured on my laptop running Gutsy and everything was fine.  However, I didn't use it for a while, so when I went to reconnect recently, it didn't connect at first due to an error on my part (I mistyped the key).  Being impatient, I decided that the fast way to correct my typo was to re-add the network, which worked at first, but after a reboot I could no longer access my WAP.  

It looks like (and I'm guessing here) that I've created two entries in NM for my WAP, and NM can't handle two identical entries.  So my question is, where is the config file (files?) for NM so that I can find that second entry and remove it?  Or is the entry stored in the gconf database?

Any help here would be appreciated.  I'm really banging my head on this one and the man pages don't seem to be very helpful.

Thank you,
Jason

---

### Post by Casual Fan on 2008-01-13
Here's another chance for me to recommend wicd instead of network manager: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Try it. You'll love it.

Or...

AFAIK, all the network manager settings are in gconf editor under system>networking>wireless>networks>(your network)

---

### Post by le_jawa on 2008-01-14
I broke down and tried it, and it is nice.  NM on Fedora servers is giving me huge fits, so I'll have to try the Fedora install too.

As for my actual problem, it turned out that my WAP needed to be power-cycled.  I don't see how it could be working all evening then crap out like that, but at least it's going again.

Thanks for the help!
-Jason

---

