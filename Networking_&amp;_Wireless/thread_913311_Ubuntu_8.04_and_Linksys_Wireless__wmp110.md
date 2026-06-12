---
title: "Ubuntu 8.04 and Linksys Wireless  wmp110"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by That 70's guy on 2008-09-07
Can't get the Internet going with this card. I have downloaded and installed ndiswrapper and installed the windows driver for the card. Network Manager sees the card and the local network but after I enter the WEP key for the network I get no connection with Firefox. I have also disabled the motherboard LAN as well but with no luck. Thanks in advance for the help.

---

### Post by king james on 2008-09-09
I have two linksys cards and I dislike them both, even in windows. I will be looking for another soon.

You may want to try to set the wep type to 64/128 HEX and enter your standard wep key.

---

### Post by lilmale1 on 2008-09-09
try finding a linux driver
and use wifi radar you cant go wrong with that

all debian file wifi radar 1.9.6

i couldn't configure network manager
i uninstalled it and install wifi.....

so get wifi radar deb or debian

---

### Post by That 70's guy on 2008-09-25
Thanks! everyone. The Wi-Fi Radar worked like a charm after changing the driver to WEXT. For anyone else you will need this software plus NDISWrapper and the current Windows driver for the card.

---

### Post by mfive on 2009-02-07
That 70's Guy... Can you elaborate on what exactly you did to make your WMP110 wireless card work??? I'm using hardy-ubuntu.

I've tried several different approaches, and searched until the end of the internet and still cannot get this card to work.

I'm using a custom built desktop PC.
I tried to follow the directions at: [http://www.linuxquestions.org/questions/debian-26/linksys-wireless-pci-672918/](http://www.linuxquestions.org/questions/debian-26/linksys-wireless-pci-672918/) using Wicd, but I still cannot manage to get a connection.

I can see two wireless networks (mine and a neighbors) and cannot connect to either of them. My router is encrypted using WPA-shared key (personal), as an fyi.

Any help would be appreciated, I'm a newbie to linux, and I'd love to get my wireless working so I can start having fun!

---

### Post by Dullstar on 2009-11-12
This isn't directly related to 8.04, but where can I find Linux drivers for this?  Seriously, it would help a lot when distro hopping.

---

