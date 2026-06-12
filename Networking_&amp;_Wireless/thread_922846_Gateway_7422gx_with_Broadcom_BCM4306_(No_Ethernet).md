---
title: "Gateway 7422gx with Broadcom BCM4306 (No Ethernet)"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by kestal on 2008-09-17
This has been solved.

I tried
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Trying%20It%20Temporarily](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Trying%20It%20Temporarily)
(Froze on the step where I had to do sudo rmmod b43). So I stoped at that step, and then did the next part.

I then created a script in init.d, like:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+4306)


Restarted. Detected. Done and Done.

---

