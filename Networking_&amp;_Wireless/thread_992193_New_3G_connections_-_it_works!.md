---
title: "New 3G connections - it works!"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Philio on 2008-11-24
I've just booted the live CD of Intrepid on my laptop to see if the new (and long awaited) 3G mobile broadband support works. I was expecting to have to call T-Mobile again and get the settings like I have to every time with Windows.

Well, it not only works, but has to be the easiest system I've ever used! No drivers required, no extra software, no settings required from network, a simple 2 step connection wizard that consists of 'Select your country', 'Select your network' and it works!

:guitar:

---

### Post by Mountford D on 2008-11-24
Great feeling when it works!

I too had success in getting my Orange Icon225 working on Ubuntu 8.04 tonight. After following instructions posted elsewhere in this forum:

[http://ubuntuforums.org/showthread.php?t=736977&page=3](http://ubuntuforums.org/showthread.php?t=736977&page=3) 

and following the Pharscape instructions:

[http://www.pharscape.org/content/view/66/53/](http://www.pharscape.org/content/view/66/53/)

I managed to get Ubuntu to recognise the modem but could not connect. The secret was to set 

APN=consumerbroadband

in conninfo.ini and comment out all the other tags - user, password, etc. I then connected using "hso_connect.sh up" and it worked! Later, I installed the "hsoconnect" GUI, set the APN property as above and blanked out the other fields.

It works like a dream. Decent speeds too, as fast as the wireless portal at my workplace accommodation and cheaper!

---

