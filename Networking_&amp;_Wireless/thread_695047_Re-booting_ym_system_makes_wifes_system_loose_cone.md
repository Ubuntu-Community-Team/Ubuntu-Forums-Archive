---
title: "Re-booting ym system makes wifes system loose conection"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by jmclein on 2008-02-12
Ok, this is a REALLY odd issue.  I am going to do my best to explain it but please bear with me. First off you should probably see the following thread as they issues are possibly connected. 

[http://ubuntuforums.org/showthread.php?p=4273755#post4273755](http://ubuntuforums.org/showthread.php?p=4273755#post4273755)

When I connect to my home network it will connect, I get 3-4 blue bars and then when I try to connect to any webpage it goes to no bars.  If I wait a few mins it will go back to three or four bars but then back to 0.

Now to the problem i was informed off today.  I rebooted my laptop (Which is the system in question) a few times and my wife says from the other room "Every time you reboot your laptop I loose my wireless connection".  That seemed a bit far fetched so I decided to test it.  She is correct.  Everytime I reboot she gets dropped.  Are the two problems connected somehow?  Or is my home network just possessed?

edit - Got a bit more info.  It seems to be when I try to connect to the wireless.  If I disable my wireless and only connect via ethernet everything is fine, she stay on line.  But the second I try to connect with my wireless she gets bumped off.

---

### Post by jmclein on 2008-02-12
Tried reseting my router and reconfiguring it again but it made no difference.

---

### Post by mkzimms on 2008-02-12
might be an issue with DHCP and conflicting IP leases.  Its weird hard reset didn't make a difference, did you roll back to factory defaults?  are either of the computers using a static IP?

---

### Post by jmclein on 2008-02-12
No, neither system is using a static IP.  When I reset I reset it to factory and then reconfigured it from the ground up.  I'm still thinking this may having something to do with my other issue but hard to say.  It's very odd to me.

---

### Post by ModelM on 2008-02-12
This doesn't sound to me like a networking problem at all but instead a radio problem. I'd try changing the channel your wireless router/access point uses.

---

