---
title: "Atheros AR5006EG dosn't work on feisty"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by darklab on 2007-07-03
Hi guys this is my first post on this forum, i have a problem with my pci wireless card, that doesn't work with midwifi and ndiswrapper but probably i have make caos in the sistems.
So i need to remove madwifi and ndiswrapper and next install the driver.
Who can help me????

---

### Post by spd106 on 2007-07-05
You can disable the madwifi driver by modifying the /etc/default/linux-restricted-modules file.
This wiki page has instruction on removing and cleaning up after ndiswrapper.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)
If you are going to re-try ndiswrapper then it's probably a good idea to download the latest version and build from source rather than rely on the older pre-packaged version.

Use this command to check the current driver in use.
```
sudo lshw -class network
```
and lsmod will show you the kernel modules currently loaded.

---

### Post by aqk on 2007-07-12
I have the same problem.

Atheros AR5006EG dosn't work on Feisty.

I currently am using a Toshiba Satellite laptop with Feisty/Vista dual boot on it.

I have installed (thru ethernet cable) all the latest 7.04 updates, including the restricted stuff, (up to June 29th), but the wireless will STILL not work.
Weird thing is, it 'sees' the essid (and any other essids lying around) but will not talk with them.

 I'm replying here thru my...uhh,  trusty Vista which had no problem with the wireless.

Any place you could point me to to somehow get this thing working? 

  Thanx.

---

### Post by slither on 2007-07-12
I have the exact same problem but with an atheros AR5005G card.

---

