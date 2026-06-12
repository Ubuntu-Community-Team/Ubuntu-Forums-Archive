---
title: "Wireless issues, Please help"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by huviduc on 2008-03-01
I am having some major issues with my wireless and can not get it to work at all. network manager from 6.06 worked PERFECT, when i upgraded to 7.10 it barely worked at all. I switched to WICD and it worked great for a long time. randomly it stopped and the service would start n boot up but icon would not show up on task bar area, but there was a blank spot for it :confused: . I can get internet through Ethernet cable fine though. Also when this, i get a black square on the desktop that randomly moves around until i Force quit the program.  I decided to uninstall and reinstall, same thing. Installed network manager, uninstalled and reinstalled WICD, same thing. I can not for the life of me, get it to work at all. Is there a way to install the OLD network manager from dapper so it works perfect again? or maybe fix WICD to work again? Please help

---

### Post by wieman01 on 2008-03-01
What wireless adapter have you got and what chipset are we talking about? Ralink by chance?

---

### Post by huviduc on 2008-03-01
I have a broadcom 43XX, My laptop battery is actually dead righyt now so i cant check exactly.

---

### Post by wieman01 on 2008-03-01
Then this is certainly the right place for you for further help:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=43XX+howto]("http://ubuntuforums.org/showthread.php?t=405990&highlight=43XX+howto")

If this one does not work for you, please check these:

[http://ubuntuforums.org/showthread.php?t=660871&highlight=43XX+howto]("http://ubuntuforums.org/showthread.php?t=660871&highlight=43XX+howto")
[http://ubuntuforums.org/showthread.php?t=475963&highlight=43XX+howto]("http://ubuntuforums.org/showthread.php?t=475963&highlight=43XX+howto")

---

### Post by goldsniper on 2008-03-01
please post 

lspci

---

### Post by wieman01 on 2008-03-01
I think this is a laptop computer so 'lspci' won't yield any results...

---

### Post by huviduc on 2008-03-01
> **wieman01 said:**
> Then this is certainly the right place for you for further help:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=43XX+howto]("http://ubuntuforums.org/showthread.php?t=405990&highlight=43XX+howto")

If this one does not work for you, please check these:

[http://ubuntuforums.org/showthread.php?t=660871&highlight=43XX+howto]("http://ubuntuforums.org/showthread.php?t=660871&highlight=43XX+howto")
[http://ubuntuforums.org/showthread.php?t=475963&highlight=43XX+howto]("http://ubuntuforums.org/showthread.php?t=475963&highlight=43XX+howto")


I have tried the first link several times, i will look into the other ones as well. Any ideas for installing the old network manager? is that possible? it works perfect for me. thanks

---

### Post by Dr Small on 2008-03-01
I used this guide to get my broadcom43xx card to work this morning:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

---

### Post by wieman01 on 2008-03-01
The old version of NM won't make much of a difference as this is an issue relating to the wireless driver. So you have to get it working first.

Please also try Dr Small's link that he kindly provided. Looks promising.

---

### Post by huviduc on 2008-03-03
well i followed the third guide that the above user posted and now my wirless and wired internet wont work ( not their fault, just stating the fact.

If i were to update to 7.10, i have 7.04, would that maybe fix it? would i lose all my beryl stuff?

If so, how do i update with out the internet?

---

### Post by huviduc on 2008-03-04
ISSUE RESOLVED. I finally got my wired internet working again, so i reinstalled everything, still no luck. But after updated everything with update manager, it started working. Thanks for the help guys

---

