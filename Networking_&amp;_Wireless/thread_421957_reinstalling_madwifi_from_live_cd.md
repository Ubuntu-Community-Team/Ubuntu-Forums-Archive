---
title: "reinstalling madwifi from live cd"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2007-04-24
hey Everyone, 

So I got Fiesty installed, my wireless card finally works properly...i got all excited and started messing around...uhhh.  So I installed aircrack and i broke my wireless I tried to fix it myself and I'm all screwed up.  I uninstalled all the madwifi drivers and now I can't get them reinstalled off live cd.

Can anyone guide me through the process of reinstalling the madiwifi drivers through live cd?  Or should I do it something else?  I have the latest fiesty release installed with a gigabyte WI01GT card  based on the atheros 5006 gs i believe.

---

### Post by stchman on 2007-04-25
> **ssc351 said:**
> hey Everyone, 

So I got Fiesty installed, my wireless card finally works properly...i got all excited and started messing around...uhhh.  So I installed aircrack and i broke my wireless I tried to fix it myself and I'm all screwed up.  I uninstalled all the madwifi drivers and now I can't get them reinstalled off live cd.

Can anyone guide me through the process of reinstalling the madiwifi drivers through live cd?  Or should I do it something else?  I have the latest fiesty release installed with a gigabyte WI01GT card  based on the atheros 5006 gs i believe.


Follow my procedure here:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

A lot of times if you install other applications or drivers they will recompile kernel modules and break the madwifi drivers.  This happened to me when I updated my ATI video drivers.  It works for Edgy and should work for Feisty.

I hope this helps.

---

### Post by Tom Fury on 2007-04-25
stchman, I just wanted to let you know that I followed your instructions and unfortunately it didn't work for me.  I have a fresh install of Feisty on an IBM T42p with an Atheros ar5212 chipset.  My wireless has been dead in the water ever since I moved to Feisty.  I'm thinking going back to Edgy since I had no problems with the wireless before.

---

### Post by stchman on 2007-04-26
> **Tom Fury said:**
> stchman, I just wanted to let you know that I followed your instructions and unfortunately it didn't work for me.  I have a fresh install of Feisty on an IBM T42p with an Atheros ar5212 chipset.  My wireless has been dead in the water ever since I moved to Feisty.  I'm thinking going back to Edgy since I had no problems with the wireless before.

That is odd as Feisty is supposed to be better with wireless than Edgy.  It looks more and more like I won't be doing the Feisty dance anytime soon.  If you are having so many problems with Feisty then a reinstall of Edgy seems to be in order.  I have lots of procedures for Edgy.  Visit my site for them.

---

### Post by Tom Fury on 2007-04-26
It's funny seeing your post now.  As I type this my laptop is reloading with Edgy.  I've had such great stability with each release that it didn't even cross my mind to image the laptop before the upgrade.  Lesson learned.

---Short time later---

Reinstall of Edgy.  Install the restricted modules and network manager.  Reboot.  I now have WPA wireless again.  I think the "improved" networking in Feisty needs some more improvement.

---

### Post by stchman on 2007-04-27
> **Tom Fury said:**
> It's funny seeing your post now.  As I type this my laptop is reloading with Edgy.  I've had such great stability with each release that it didn't even cross my mind to image the laptop before the upgrade.  Lesson learned.

---Short time later---

Reinstall of Edgy.  Install the restricted modules and network manager.  Reboot.  I now have WPA wireless again.  I think the "improved" networking in Feisty needs some more improvement.

I am going to wait a couple of months for Feisty to improve or wait for Gusty.  I am having great stability with Edgy so no change is needed.

---

