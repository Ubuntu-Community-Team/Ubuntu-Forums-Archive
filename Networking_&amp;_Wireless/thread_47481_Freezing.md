---
title: "Freezing"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by Yoshiassasin on 2005-07-08
I am relatively new to Linux, and have just installed Ubuntu on my PC. I have a wireless network with a D-Link DWL-G510 pci card installed. I used Ndiswrapper to install the drivers, and Ubuntu recognized it and everything. Now, when I go to Network Settings, select wireless connection (wlan0), type in ESSID and the WEP key, set it to DHCP, and then activate it, the computer freezes. The mouse doesn't respond, and neither does the keyboard. When I look at the wireless pci card though, I can see that the light in the back starts blinking constantly when I activate it. Before that, the light is comletely off. I have searched for this and have seen other people with the same problem, but misteriously, they all have not been answered to the point that I can fix my problem. 
Maybe I'm not looking hard enough, but I want someone to help me.
Thanks.

---

### Post by spd106 on 2005-07-09
Hi, did you compile ndiswrapper from source or use the ndiswrapper-utils package from the repo?

It sounds like the kernel is crashing. This could be caused by the ndiswrapper module behaving wrong or the wrong driver. On the ndiswrapper website it lists two versions of the DWL-510. I suggest you make sure you know which one you have, ie $lspci.

You could also try entering the config details at the cl, ie iwconfig or edit the /etc/network/interfaces file.

Hope this helps

---

### Post by Yoshiassasin on 2005-07-09
Thanks. I downoaded ndiswrapper from sourceforge, and my adapter is the first one. I checked. I'll try what you said, and hopefully It will work.

---

### Post by Yoshiassasin on 2005-07-10
Well, I still can't figure out whats wrong, but when I type in iwconfig, this comes up.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

Can this be the key to solving my problem?

---

### Post by spd106 on 2005-07-11
It should be okay, i had that error when i loaded my card in mandrake 2005SE. The card worked fine it's just that some of the stats like signal strength might not work.

Have you seen this website?
[http://www.xs4all.nl/~bsamwel/dwl-510-on-linux-2.6.html](http://www.xs4all.nl/~bsamwel/dwl-510-on-linux-2.6.html)
It suggests that there is a linux drivers for the dwl-510. You should check that it uses the same chipset though and I would have thought this would be included in Hoary.

Good luck

---

