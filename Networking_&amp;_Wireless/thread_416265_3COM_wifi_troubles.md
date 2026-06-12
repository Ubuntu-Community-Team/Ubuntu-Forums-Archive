---
title: "3COM wifi troubles"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by SiN486 on 2007-04-21
My 3com 3CRWE154G72 version 1.0 isn't going into monitor mode. In edgy this card worked flawlessly, clean install and it just worked, though in feisty it won't start in monitor mode.

I've noticed that the card is being assigned to 'wlan0' and 'wmaster0' instead of plain old easy 'eth1'. So feisty has changed something that was working perfectly in edgy.

Hopefully I don't have to reinstall back to edgy...

---

### Post by druhboruch on 2007-04-21
I have exactly the same card and the same problems.
Somehow I got it to work, but it is very temperamental.  I have to manually connect after each reboot.

It used to be eth1, now it is vlan0 and wmaster0.  (???)

To get it to work I removed everything from iftab and in interfaces I left only lo lines.

If SSID broadcast on the AP is disabled, it would not work at all.

---

### Post by SiN486 on 2007-04-22
I was just trying to get the card into monitor mode and thought everything else was fine, but now I realise i cannot get the card to connect to my AP at all (while my onboard wifi connects flawlessly).

I did get it to connect once, but I cannot reproduce it.

I've been looking around at ww.prism54.org and looking at ndiswrapper, but I shouldn't be. This card worked fine in Edgy!!!!!

---

