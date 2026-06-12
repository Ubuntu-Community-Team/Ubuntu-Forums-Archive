---
title: "No wireless: WNA3100"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by aedan2 on 2015-04-26
So... I couldn't get it to work. in stead could some one tell me about any pci-e/usb wi-fi adapter that works with ubuntu "Out of the box"?

---

### Post by Geoffrey_Arndt on 2015-04-26
If the netgear router is generating a wireless signal, then, you can plug in a usb-wireless adapter (works with laptops or desktops).   Here is a model that will work out of the box with Linux:  No drivers needed!

[http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_3?ie=UTF8&qid=1430104441&sr=8-3&keywords=panda+wireless+usb+adapter](http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_3?ie=UTF8&qid=1430104441&sr=8-3&keywords=panda+wireless+usb+adapter)

---

### Post by sandyd on 2015-04-26
Seems to only work with ndiswrapper
[http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

---

### Post by Bucky Ball on 2015-04-27
*Thread moved to **Networking & Wireless**.*

I've changed your thread title and moved your thread to improve your chances of support. Generic thread titles like 'Help!' are discouraged as they tell potential helpers nothing about your issue and the majority of folk here want help. ;)

Good luck with it. As you've found, that card is problematic in Ubuntu. I would be tempted to get a cheapie USB dongle that will work 'out of the box'. 'OOTB' support for the WNA3100 may arrive one of these days but it hasn't to this point and that card has been out for quite some time.

---

### Post by aedan2 on 2015-04-28
*Bucky Ball*


Thanks for helping with my post and for the idea

---

### Post by Bucky Ball on 2015-04-28
All good. As sandyd has mentioned and linked to, it will work with ndiswrapper, one of the few cards it is still used for. Give that link a go and see if you can get things working. Good luck.

---

### Post by FalCT60 on 2015-04-28
Hello,
If you're running 14.04 LTS this stick (amongst others) **_won't work at all_**, whatever the method you try (unsure for upper versions, just writing about 14.04 LTS).
In fact, it seems there are less things that work with 14.04 LTS compared to 12.04 LTS.

---

