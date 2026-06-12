---
title: "Slow wireless connection"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by ALzir on 2007-11-14
Hi, I've got a HP compaq nx9005 laptop that I have been trying to install gusty on. Everything has gone well up to now but I'm stuck trying to set up the wireless card. When I installed ubuntu the wireless card was detected and I enabled the restricted driver. I connected to the net through the wireless and it worked fine. The internet was at normal speed and I could see the samba share on my file server.

When I restarted the computer my wireless connection became really slow and I can no longer see the samba share on my file server, also an ubuntu box. When I disable the wireless and go back to the cable my speed goes back to normal but I still cant see the windows network with my samba share any more.

My best guess is its a setting somewhere that gets overwritten when the computer reboots but I don't really know what I'm doing when it comes to networking and have no idea where to go from here.

If someone could point me in the right direction it would be really appreciated.

---

### Post by ALzir on 2007-11-14
Hello again,

 I've fixed it. :)

 I disabled the restricted driver and installed it manually following this guide, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The reason I couldn't see my samba share from the wireless network was because I had set the samba to not accept connections from the wireless network. Totally forgot I did that its at the end of the samba setup guide I used to get the file server working,

 [http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+samba) :lolflag:

---

