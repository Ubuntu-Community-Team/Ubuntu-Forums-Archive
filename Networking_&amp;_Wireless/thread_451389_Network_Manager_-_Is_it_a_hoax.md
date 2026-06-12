---
title: "Network Manager - Is it a hoax?"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by EarlGreyIII on 2007-05-22
OK, I give up :(

The main reason I had for upgrading to Fiesty 7.04 was the cool looking Network Manager that would allow me to connect using WPA.

According to the Add/Remove utility Network Manager is installed, and apparently I have something called a supplicant lurking about in there too.

But I cant find the thing anywhere? In my 'Start' menu I have **System -> Administration -> Network**, but this seems to be the same old WEP application, no WPA option (and it doesnt look like the gui in the 'Upgrade to 7.4' pics)

I tried to find how to launch it from the command line, but to no avail after reading the posts here so far.

Heeeelp:confused:

Tell me the Network Manager isn't just a hoax to wind up us newbies?

Cheers
Andrew.

---

### Post by blazercist on 2007-05-22
you're kidding right?  that is the network manager, its no hoax as it supports many more wifi cards than it did in previous versions... as far as WPA i dunno i never used it.  WEP is more or less working...

---

### Post by chili555 on 2007-05-22
Do you not see five progressively larger bars in your panel up top? Click on that little icon. That's the NM applet.

"Start menu"? Step 2 of your 12-step Windows Recovery Program reminds us not to use Windows terms for Linux things.

---

### Post by EarlGreyIII on 2007-05-22
Haha, I just knew I would get in trouble for the 'Start' thing. OK, I knew I was doing wrong, hence the 'quotes';) So what do we call it in this brave new world? Circle thingy?

Anyhows off the point there. Well yep, i see an icon that looks like that, and yes it does give me signal strength. Also I see my wireless adapter (D-Link DWL-G650+ pcmcia adaper) lights flashing, so I guess the driver is talking at least.

However I only get options for WEP Hex or WEP ascii for authentication keys, I was kinda expecting that to be ammended with WPA options. Do i need to download some more tools to enable that?  

OK, I could just reconfigure my wireless hub to use WEP, that was my next option after this post. (which will involve a too long discussion with my girlfriend over why I'm reconfiguring her windows lappie too, hence the deliberation)

Ta
Andrew

---

### Post by chili555 on 2007-05-22
Is your card capable of WPA? You can find out with:```
sudo iwlist eth1 key
```Substitute your wireless interface if it's not eth1.

---

### Post by Dylnuge on 2007-05-22
Off topic, we calll it the Applications, Places, and System buttons. The bar itself it just the menu bar.

---

### Post by ugm6hr on 2007-05-22
> **EarlGreyIII said:**
> 

**However I only get options for WEP Hex or WEP ascii for authentication keys, I was kinda expecting that to be ammended with WPA options. Do i need to download some more tools to enable that?  **



In this page with those options - click "enable roaming mode".  And then OK.
Then right-click on the nm-applet icon in Sys-tray (the 4 small grey rectangles that say something like "No Network" when you hover over it).  Make sure "Enable Networking" and "Enable wireless" are ticked.
Then left-click the same icon.  You chould now see a list of wireless networks that broadcast an SSID - just click on yours and it should automatically ask for a WPA password if its a WPA network.  If your router doesn't broadcast SSID, you have to "Connect to other wireless network.." - but I've not tried this.

---

### Post by Dylnuge on 2007-05-22
WPA and WPA2 Personal and Enterprise are supported.

---

### Post by Craigus on 2007-05-26
The built in acx driver does not support WPA unfortunately (assuming that your card isn't Rev E1 without the Texas chipset), that's why the option isn't available.

See this thread for some information:

[http://ubuntuforums.org/showthread.php?t=422725&highlight=g650+wpa](http://ubuntuforums.org/showthread.php?t=422725&highlight=g650+wpa)

You'll have to use ndiswrapper and a windows driver for the card.

I still don't have mine running reliably.

---

### Post by jwelsh405 on 2007-05-26
when you updated to feisty in your network preference does it not allow roaming

---

