---
title: "Wireless connection slower in ubuntu than in vista"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by JanRa on 2008-08-02
Hello all,

I just bought myself a wireless router D-link dir 635 which is a 802.11N router. I installed it and under VISTA my laptop picks it up and I get a connection speed of 144 Mbps. However under Ubuntu Hardy Heron I only get a speed of 54 Mbps.
I have no idea what the reason for this is. Can anybody help?

Thanks alot,

Jan

---

### Post by JanRa on 2008-08-03
nobody knows anything about this?

---

### Post by TDragon on 2008-08-11
> **JanRa said:**
> nobody knows anything about this?
 
 
From what I understand, and this has been mentioned in other threads, 802.11n (300mb) is NOT supported at this time. Therefore, your card is only connecting with 802.11g (54mb).
 
This is the case regardles of what driver you are using.
 
 
Also, you may want to look into why you are not receiving the full 300mb speeds that your N card is capable of. Of course, if you are too far away from your router (w/ all of walls, etc in between), it may be the culprit (for Vista that is).

---

### Post by TDragon on 2008-08-12
According to this thread, these Ubuntu mac users are using another driver based off of the ath9k source. Apparently, this driver is capable of 802.11n. How true this statement is, I don't know. However, I may give it a shot.
 
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) <- Driver website
 
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097) <- Thread

---

