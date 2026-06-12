---
title: "Wireless Issues in Linux"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Silvo on 2007-05-11
G'day!

I am using Feisty Fawn Ubuntu, and am trying to connect to my wireless network. I am using WEP encryption, and was using a static IP address, but I thought that may have been causing troubles so reverted to DHCP. 

Ubuntu successfully detects and loads drivers for my wireless card (first Linux distro that has), and I can see both my wireless network and that of a neighbour's. When I try to connect to it, however, (using roaming mode) it will ask me for my WEP key, which I supply, and then wait a bit. After about 30sec - 1min, it will ask again, and this will repeat. It does not ever successfully connect to my network. If I turn roaming off and manually specify the details, it still does not work.

I have used Suse 10.1 and Knoppix 4.something, and neither has been able to connect either. I guess what I am asking is what is my next step in getting Ubuntu to work? I suppose I could disable WEP, but I don't really want to. It could also be more trouble than it is worth, as to my understanding, Ubuntu doesn't have a problem with WEP, but with WPA. Is that right?

Please help!

---

### Post by RichPicker on 2007-05-11
Don't know if it will help, but I use "wifi-radar" and/or "Wireless Assistant" 
Both are available in Synaptic Package Manager

---

### Post by Emeriz on 2007-05-11
wicd is working very well for me.  I fought through several issues with WEP and WPA and once I converted to wicd I haven't had any issues so far, but YMMV.

 [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Em

---

### Post by Silvo on 2007-05-11
So by the sounds of things you think the problem is with the connection thing I am using and not the settings  am using?

I will try those mentioned, thank you!

---

### Post by Silvo on 2007-05-11
Well I tried wicd, but there was some python errors that I don't understand. I tried to install wifi-radar from a .deb that I obtained previously but it required something called "menu". 

I will now check to see if there is a specific Ubuntu distribution of wifi-radar.

Also, how do I turn off the network-manager?

---

### Post by Silvo on 2007-05-12
OK, I obtained wifi-radar for Ubuntu, which will not connect to the wireless network. I figured out what was wrong with wicd, but it doesnt want to connect either. 

So, what next?

---

### Post by Emeriz on 2007-05-15
Okay, I looked back over your post and if you are having issues with Knoppix and SuSe as well, then it may  be driver related. I just suggested the move to Wicd as it made seeing things simpler for me, but they are really all just front-ends for the underlying apps.   

What wireless card are you using?  Its possible the card has drivers but they are not fully functional, so NDISWrapper may be the way to go.  Have you googled/searched the forums for your particular card?

Em

---

