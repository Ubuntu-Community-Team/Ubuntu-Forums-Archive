---
title: "Broadcom 1370 wireless Dell laptop problems"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by jester805 on 2007-04-23
I installed 7.04 on my Inspiron B130 over the weekend.  It has the Broadcom 1370 wireless card built-in.  I read posts were people installed WICD and that fixed their problems.  I tried that and it seemed to help, but I'm still not up and running.

After installing WICD and rebooting, the DHCP found my router as a DNS server.  It still won't connect to my wireless network and I keep getting a 169.254.x.x IP address.

Any ideas / suggestions?

Thanks!

---

### Post by p252 on 2007-04-23
I have a Dell Inspirion B130 too. Ubuntu in all flavors has worked like a charm with it. Wireless as you know takes some tweaking, but I have gotten to where I get it working quite easily (with the exception of a recent problem which can be seen in the networking and wireless section of the forum). I did a clean install of Feisty 7.04. To get my wireless working I use ndiswrapper and the instructions found here [http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm+4306) and the drivers i took from the package found here [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm+4318) Keep in mind that feisty has Network Manager already installed so you don't need to do that step. (also, for some reason wpa2 doesn't work with feisty for some reason, though wpa works just fine for me). Hope this helps.

---

### Post by jester805 on 2007-04-25
Thanks for the help!  I tried doing that, but wasn't able to get it working.  I didn't spend a whole lot of time on it so maybe I can try again tonight.

---

### Post by jester805 on 2007-04-25
The second link you gave me worked like a charm!  Thank you so much for your help! :guitar:

---

