---
title: "Broadcom BCM4312 monitor mode"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by wiz561 on 2008-09-23
Hi!

I'm attempting to use the internal Dell Wireless 1395 WLAN Mini-Card with Kismet and Aircrack, but I'm running into some problems.  Basically, I can't get the driver to go into sniffing/monitor mode.  The network card is an internal one from dell; Ubuntu says it's a BCM4312, but the device ID is 14e4:4315.

It seems like the card likes to use the 'wl' module instead of b43, which is what I would like for it to use.  I was wondering, how do I get Ubuntu to use the b43 module instead of wl?


Thanks in advanced...

---

### Post by Ayuthia on 2008-09-23
> **wiz561 said:**
> Hi!

I'm attempting to use the internal Dell Wireless 1395 WLAN Mini-Card with Kismet and Aircrack, but I'm running into some problems.  Basically, I can't get the driver to go into sniffing/monitor mode.  The network card is an internal one from dell; Ubuntu says it's a BCM4312, but the device ID is 14e4:4315.

It seems like the card likes to use the 'wl' module instead of b43, which is what I would like for it to use.  I was wondering, how do I get Ubuntu to use the b43 module instead of wl?


Thanks in advanced...
The b43 module does not work with your card at this time so even if you did install it, it will not work.  The b43 developers are working on it though.

---

### Post by willca on 2008-09-24
Try using ndiswrapper instead.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Just browse for it. This guide works even if you have Gutsy or Hardy.

---

### Post by Ayuthia on 2008-09-24
> **willca said:**
> Try using ndiswrapper instead.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Just browse for it. This guide works even if you have Gutsy or Hardy.

Unfortunately, ndiswrapper is not one of the native modules so kismet and aircrack will not work with it.

---

### Post by wiz561 on 2008-09-24
Thanks for the information.  I had a feeling the b43 driver wouldn't work with the card yet.  :(  I suppose I will just wait or scrounge around for another card.

As for the ndiswrapper, unfortunately, Kismet does not work with it.  

Thanks!

---

### Post by Junglizer on 2008-09-24
I'd recommend trying to pick up a card chipped with an AR5213/2 (often listed as AR5004 as thats the family its from.) These are excellent.

---

### Post by rjr162 on 2008-11-07
please check this post:
[http://ubuntuforums.org/showthread.php?p=6120811](http://ubuntuforums.org/showthread.php?p=6120811)

I got monitor mode working on a broadcom in a Dell Inspiron E1505 under Ubuntu 8.10.  It works better for me than monitor mode did in 8.04.  I can enter monitor mode and sniff, and still use the wireless manager to connect and stay connected to a wireless AP to hit up the web.

---

### Post by thskat on 2011-04-02
i have the same problem with bcm43225, anyone have a solution ?
//ops old thread

---

