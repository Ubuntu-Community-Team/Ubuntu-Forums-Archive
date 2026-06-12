---
title: "WiFi troubles on my desktop. Any help!!!"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by vivekrawal on 2005-12-05
I have Desktop with 'AMD athlon 2400' and have recently installed breezy.
i have ZyAir G 200 wireless USB adapter.  I do not think it is linux compatible. So i installed ndiswrapper from the breezy CD. I then further installed the drivers from ZyAir CD (could not figure out from the list on the ndiswrapper site). now when i give command ndiswrapper -l it shows me installed driver present hardware present. but in system>administration>networking i do not see any wireless connection that i can enable. 

can any one help? I am new to linux so step by step help will be useful.
Thanks in advance
Vivek

---

### Post by wbiggers on 2005-12-05
I'm not sure I can help with specifics you have here - but check out the wiki pages on [www.ubuntulinux.org](www.ubuntulinux.org).  Click on the wiki tab on the right side of the home page.  Type in WiFi in the search box and it should show you some interesting pages that will help you find more information on this issue.

I've had a frustrating time with WiFi cards.  The only one I've found to truely work 'out-of-the-box' as advertised is the Netgear WG311T.  However, there are many who know much more than I do on how to get unsupported cards to work.

---

### Post by carlosqueso on 2005-12-05
did you make sure to use 
```
 sudo modprobe ndiswrapper 
```
after you installed the driver?  You need to do that each time you boot to even be able to see the card.  However, if you type 
```
sudo ndiswrapper -m
``` it should be working on startup.

---

### Post by vivekrawal on 2005-12-05
I have tried both the commands. But I can not see any wlan0 option in network-admin. 
ndiswrapper -l
shows me that driver is present, hardware present.

but still wi-fi is not enabled.

any more clues?
Vivek

[QUOTE=carlosqueso]did you make sure to use 
```
 sudo modprobe ndiswrapper 
```
after you installed the driver?  You need to do that each time you boot to even be able to see the card.  However, if you type 
```
sudo ndiswrapper -m
``` it should be working on startup.[/QUOTE]

---

