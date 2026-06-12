---
title: "connecting smartphone for internet sharing"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by Inisfad on 2011-02-26
Been studying this, and seem to be getting nowhere.  I am running Ubuntu 9.10, and just got a Nokia E5 smartphone.  I want to share my computer's internet connection (no router) with the smartphone. Can anyone simply describe how to do this, so that when my laptop is on the internet, I can share that internet connection with the phone?  I have dmasq installed, and have tried making a new wireless connection (no security, etc.). When I do this, network manager spins around, and my phone sees the new connection. The phone only sees the connection as long as the network manager icon is spinning.   The phone allows me to try to hook up to the internet, but does not go on to any internet page, and says 'invalid server'.  At some point, network manager stops spinning, 'phone disconnected' comes up on network manager, and the connection is lost.  Any ideas?  (please give any advice as though you were talking to an idiot....)  Thanks!

---

### Post by pi.boy.travis on 2011-02-26
> **Inisfad said:**
> Been studying this, and seem to be getting nowhere.  I am running Ubuntu 9.10, and just got a Nokia E5 smartphone.  I want to share my computer's internet connection (no router) with the smartphone. Can anyone simply describe how to do this, so that when my laptop is on the internet, I can share that internet connection with the phone?  I have dmasq installed, and have tried making a new wireless connection (no security, etc.). When I do this, network manager spins around, and my phone sees the new connection. The phone only sees the connection as long as the network manager icon is spinning.   The phone allows me to try to hook up to the internet, but does not go on to any internet page, and says 'invalid server'.  At some point, network manager stops spinning, 'phone disconnected' comes up on network manager, and the connection is lost.  Any ideas?  (please give any advice as though you were talking to an idiot....)  Thanks!

I *believe* this is a bug in network-manager, as I seem to remember connection sharing working for me only since 10.04. Might I recommend an upgrade?

---

### Post by Inisfad on 2011-02-26
Eck I have Karmic fine tuned to exactly the way I want it.  Have been stalling on the upgrade issue.  That being said, what about making my computer an access point, or is this whole issue governed by the bug in network manager??  Thanks.

---

### Post by pi.boy.travis on 2011-02-26
> **Inisfad said:**
> Eck I have Karmic fine tuned to exactly the way I want it.  Have been stalling on the upgrade issue.  That being said, what about making my computer an access point, or is this whole issue governed by the bug in network manager??  Thanks.

The bug prevents network manager from interfacing with the utilities that provide the ad-hoc routing capabilities. If you use Update Manager to perform the upgrade, any customizations/configuration should be preserved; I have systems that have been upgraded since 7.04.

---

### Post by Inisfad on 2011-02-27
Well, it turns out that there is no upgraded needed.  Just in case anyone else needs to do this, after DAYS of searching on the internet, and reading HUGE scripts that may or may not work, the fix was actually quite simple.  You must have dnsmasq-base installed, and remove dnsmasq.  That's it.  Then just make your adhoc connection, easy peasy, all done, and network manager connects your iphone, smartphone, whatever, to your new connection.  Thanks for your responses, though!!

---

### Post by stevenwscott on 2011-05-02
I have it working, and Lucid 10.04 still hasn't gotten connection sharing right. See--> [http://ubuntuforums.org/showpost.php?p=10757443&postcount=19](http://ubuntuforums.org/showpost.php?p=10757443&postcount=19)

SWS

---

### Post by Inisfad on 2011-05-02
As a real newbie, I didn't go through any of the process above. Just removed dnsmasq, etc. as above post.  The connection works, although there are times that I have to make a new wireless network as Lucid won't connect to the old one.  But it is working well enough for me.  Now my problem is that bluetooth has suddenly stopped working.  Had none of these problems with Karmic.......

---

