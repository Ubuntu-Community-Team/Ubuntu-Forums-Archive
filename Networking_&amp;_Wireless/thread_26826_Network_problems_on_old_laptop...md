---
title: "Network problems on old laptop.."
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by Provo on 2005-04-14
I'm a total newbie to linux, so the answer for this might be devastatingly simple..
Here goes; I've installed Ubuntu on an old Acer TravelMate 514TXV laptop, and I'm using a D-Link DWL-G650+ Wlan card.. But I'm having some problems..
What's strange is that Ubuntu finds the card, cause it shows in Device Manager. In Network Settings it says (when card is in) Wireless Connection, The interface wlan0 is active. Well, first it said "not configured", but i clicked properties, and ticked "This device is configured", typed in the ESSID of my wireless network, and set Configuration to DHCP. (Don't know if just ticking "This device is configured" without actually having configured anything could be the problem..?)
So the card is found, and the interface is up and responding to the presence of the card. But the led's on the card do not light up at any time, and when doing "iwlist wlan0 scan" it's extremely quick at telling me "No scan results". It seems that it finds the card, but just doesn't feel like using it...
Any help would be greatly appreciated! Remember I'm a newbie..  :wink: 
By the way, there's nothing wrong with the card, because it worked fine with windows 1 hour earlier..

---

### Post by erkki70 on 2005-04-14
Hi,
You should have a look here for a start:
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)
Also:
[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)
Maybe something usefu here too:
[http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html](http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html)

Hope this helps and good luck!

Cheers,
Erkki

---

### Post by Provo on 2005-04-19
Thank you!
I'm now several steps further on my way to get this working! Now my problem is as follows; If I insert my wlan card before boot, it's completely dead, just as I described earlier. And if I insert it after it's booted, the screen turns black, with a small dos-like marker in the top left corner. So I need to insert it while it's done most of the booting, but not all, to get it to work. This is a little annoying, to say at least..
I'm using ndiswrapper, and win2k version of the driver. Any help in this subject would be greatly appreciated.
(Still a newbie, remember!  ;-) Explain things as I was 4 years old.. )

---

