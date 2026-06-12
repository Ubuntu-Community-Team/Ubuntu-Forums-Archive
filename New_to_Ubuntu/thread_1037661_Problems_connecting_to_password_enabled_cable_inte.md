---
title: "Problems connecting to password enabled cable internet"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Beatbreaker on 2009-01-12
Hi, as the subject says i'm having Problems connecting to password enabled cable internet connection. 

I'm using XP as well and i typed in my user name and password the the internet connection the same as i did in XP as i did Ubuntu but Ubuntu will not work. I'm not sure if i'm making a mistake with the settings

I'm living in Japan, and trying to connect to OCN (Flets - NTT)

[[IMG]http://img156.imageshack.us/img156/8103/screenshotconnectto8021aa8.th.png[/IMG]](http://img156.imageshack.us/my.php?image=screenshotconnectto8021aa8.png)

---

### Post by aesis05401 on 2009-01-12
Hi,

If you are using Intrepid then you are not alone with this issue.  I've noticed a number or threads related to this on other sites as well as unanswered ones like this from this website: _[http://ubuntuforums.org/showthread.php?p=6012327]("http://ubuntuforums.org/showthread.php?p=6012327")_. 

This post from the OpenSuSe forums includes an Ubuntu script that apparently worked for what this poster wanted using WPA-EAP and explicitly defining the certificate:_[http://forums.opensuse.org/network-internet/402625-802-1x-wired-network-security.html]("http://forums.opensuse.org/network-internet/402625-802-1x-wired-network-security.html")_

The details are always a little different, but most of the posts I saw suggested that Hardy works fine with the authentication you are attempting to perform.  I also saw a suggestion of replacing Network Manager with alternative tools, but this seems kinda prone to unintended consequences.

If you are interested in this then here is a link to some instructions for replacing NM: _[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html]("http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html")_

I would like to add one point, though.  802.1X on a wired network is known to be inherently flawed and open to MITM due to the fact that wired 802.1X only authenticates when the session is initiated.  Wireless 802.1X does not have this flaw... just in case you weren't aware ;)

---

### Post by Beatbreaker on 2009-07-31
i'm not going to mark this as solved because to me it's not. I ended up moving house and now i don't have password enabled cable internet so the issue was worked around.

This problem was a complete show stopper for me and i went straight back to XP during that time. I found it surprising that something so fundamental was overlooked and then required scripts and good fortune to get working.

---

