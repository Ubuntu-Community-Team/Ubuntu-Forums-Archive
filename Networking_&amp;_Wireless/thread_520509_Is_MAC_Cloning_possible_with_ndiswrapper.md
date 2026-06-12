---
title: "Is MAC Cloning possible with ndiswrapper?"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-08
Currently using ndiswrapper 1.48rctl.  Ive tried cloning my mac address with following statment:

```
sudo iwconfig wlan0 down
sudo iwconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
sudo iwconfig wlan0 up
sudo dhclient wlan0
```

That doesnt seem to work.  

Ive looked in the /etc/ndiswrapper/lsbcmnds folder.  There are 5 different conf files present -- all have the same content, no mac address is listed in any of these files.  Do I need to add a statment within these files or do something else??

---

### Post by spd106 on 2007-08-08
It doesn't always work that way, try using macchanger instead.

---

### Post by kevdog on 2007-08-08
Any tips on how to do this??

I first tried 
macchanger -s wlan0 
to show current mac address.

I then issued command
sudo macchanger -r wlan0
It stated the Fake MAC address

But then when I checked:
macchanger -s wlan0
It showed the original mac address -- nothing was changed!!

---

### Post by spd106 on 2007-08-08
It's been a while since I used macchanger so I have had a quick look and found that it doesn't seem to work with Ndiswrapper, it doesn't with my Broadcom card anyway.

It works fine with madwifi on my Atheros wifi card (though it won't connect to my AP) and with bcm43xx on the Broadcom card (does connect).

---

### Post by kevdog on 2007-08-08
I read a post stating to change the mac address within the conf files located in the /etc/ndiswrapper/<directory>/ directory.  I looked at the 3 conf files.  Although each had a different name, all three had the same information.  There was no mac address|<.....> line in any of these files.

Any suggestions??? Im running ndiswrapper/broadcom 4306.

---

### Post by Austin_KW on 2007-08-08
> **kevdog said:**
> Currently using ndiswrapper 1.48rctl.  Ive tried cloning my mac address with following statment:

```
sudo iwconfig wlan0 down
sudo iwconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
sudo iwconfig wlan0 up
sudo dhclient wlan0
```

That doesnt seem to work.  

Ive looked in the /etc/ndiswrapper/lsbcmnds folder.  There are 5 different conf files present -- all have the same content, no mac address is listed in any of these files.  Do I need to add a statment within these files or do something else??

Is that a typo in you post or in your interfaces file; should be ifconfig not iwconfig

---

### Post by kevdog on 2007-08-08
Austin -- you are correct about the typo.  I went back and used ifconfig - still the same result (I might have done this the first time but posted in incorrectly).  Im certainly striking out on how to do this with broadcom/ndiswrapper.

---

