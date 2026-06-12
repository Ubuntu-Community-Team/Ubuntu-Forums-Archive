---
title: "&quot;Wrong&quot; wireless network invariably selected on boot"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-10-24
Upgraded to Gutsy on my MacBook (C2D) last week and nearly everything works perfectly.
I used this [guide]("https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688") to install the madwifi driver for the wireless connection. While this works fine once it's set up, it takes a little effort to get it going on boot up.
Where I live, about 10-12 wireless networks are picked up by my network card (Atheros chipset). However, only one of these (my own) is of any use to me.
Strangely, on boot, nm-applet selects the SECOND strongest wireless signal to try to connect to, and ignores the signal from my own router which is 3-4 times stronger. So, then I have to try to click into the radio button for my own network. This is surprisingly difficult and may take 3-6 clicks until it's accepted and a request for the password for the keyring comes up.
What's up with this?

---

### Post by Jeff250 on 2007-10-24
If you need to remove a preferred network from network manager, you can do so by using gconf-editor and navigating to the following key:
/system/networking/wireless/networks
Inside of there, you should see the network that you don't want to be automatically connecting to, so go inside of the respective key and right click all values and unset all of the keys in it.

---

### Post by PaulFXH on 2007-10-24
That worked perfectly!
Thank you very much.
Paul

---

