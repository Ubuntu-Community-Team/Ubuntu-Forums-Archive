---
title: "Wireless no longer fuctioning"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by GMUDuckman on 2006-11-03
I recently did a clean install of Edgy. In both Edgy and Dapper I've had a tremendous amount of trouble with my wireless. My card is a Broadcom BCM4306. I finally found a tutorial that made my wireless work with network-manager-gnome!([http://ubuntuforums.org/showthread.php?t=280962]("http://ubuntuforums.org/showthread.php?t=280962"))HOWEVER, I restart and I am no longer able to connect to the wireless networks. The only thing I did after doing the tutorial was install beryl, however I don't see how that would have anything to do with my wireless network.  I can still see my Networks but when I click on join other network and type in my network EXACTLY how it should be I can't connect. It tries to connect for a little bit but then just poops out and I get the little monitors with the orange !.  I tried clicking on the network I see in network manager. Same thing.  I tried redoing the tutorial. Nothing.  On the first try when I connect network manager's lower orb goes green... but it still doesnt completely connect.  Then when I try a second time it doesn't go green at all.  I try connecting via network setting. Nothing. Please please please someone help me. I love ubuntu but if I cannot get the wireless to work it is practically useless to me, since the only place i have wired network available is at work. And i'm there maybe 4% of the time. I am willing to send any documentation you need at all! Just please respond

---

### Post by Epperly on 2006-11-03
another bcm4306... whoever makes this card and doesn't have linux drivers fuckin sucks... way to make things hard for so many people.

---

### Post by GMUDuckman on 2006-11-03
LOL Broadcom made it, i had it working! and when it was working it was so nice... but it just stopped... and now i'm sad

---

### Post by Epperly on 2006-11-04
I finally just got my bcm4306 working thanks to this tutorial:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx)
But, I use Dapper(>Edgy :p)
It stopped working when you upgraded to Edgy?

---

### Post by squibT on 2006-11-04
Startup wl networking at login...

Add the line: "/etc/init.d/networking restart" (sudo not needed, no quotes) to /etc/rc.local. This will run at startup. No permission changes needed on rc.local file either.

---

### Post by GMUDuckman on 2006-11-05
> **Epperly said:**
> I finally just got my bcm4306 working thanks to this tutorial:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx)
But, I use Dapper(>Edgy :p)
It stopped working when you upgraded to Edgy?

I finally got it work... had to use NDISWrapper 1.8 like they stated later in the thread... work magnificently! I'm very happy!
And I'm still using edgy... it works in edgy too!!!!!

---

### Post by Epperly on 2006-11-05
Sweet,  good to hear.

---

