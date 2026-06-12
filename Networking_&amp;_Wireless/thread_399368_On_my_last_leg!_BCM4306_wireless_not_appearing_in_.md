---
title: "On my last leg! BCM4306 wireless not appearing in Network Manager"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by SATTI on 2007-04-02
I have been trying to get my wireless to work for almost 3 days now, I first migrated to Pclinuxos and the Internet worked, but to no avail my USB sound wouldn't worked.

So, i tried 7.04 feisty, the sound works (Hurray) but the wireless doesn't work. This is driving me insane, I'm on the brink of returning to windows.

I have read many guides, tried ndiswrapper again and again...but no luck. 

I'm trying to now download the 80211g.zip file from acer as illustrated on the site;

(ctrl+f <VOYAGER>)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

But the link is dead, i have also tried on Acer's website but the flash also seems to be down.

I know i have to install the bcmwl5a version, but the one i have on my ubuntu box doesn't seem to work. I followed the guides, i blacklisted the bcm43xx driver, did all the sudo commands, but my driver wont appear in the network manager.

All i have in there is a wired connection, and a modem connection.

Somebody PLEASE help me, I have searched the forum high and low,

I really want to use this, 

Thankyou!

Stephen.

---

### Post by Kobalt on 2007-04-02
Could you please post the output of this command line : 
```
iwconfig
```

---

