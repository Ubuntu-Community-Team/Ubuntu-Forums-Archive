---
title: "Networking from Live Feisty CD?"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Gus_T_Reer on 2007-06-26
Hi all,

Sorry, complete network noob here.

I'm trying to give a demo of Feisty on a laptop using the Live CD and I would like to get the networking going if at all possible. The laptop uses a wireless Belkin F5D7010 PCMCIA card on a Broadcom BCM4306 LAN Controller.
Looking at [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin) I can see that it is possible to get things working and I'm keeping track of this thread [http://ubuntuforums.org/showthread.php?t=484082](http://ubuntuforums.org/showthread.php?t=484082)

I have 2 questions: Is it possible to get the laptop networked using the Live cd, ie. not actually installing Ubuntu? And if so, then can someone lead me through it please?

At the moment I can't even seem to get ndiswrapper installed off the live cd.

Thanks for any information.

---

### Post by kevdog on 2007-06-26
Im not sure about question #1, I think a full installation is needed but I could be wrong.  
#2 - ndiswrapper is not on the LiveCD.

---

### Post by Yoooder on 2007-06-26
1) Yes, you can use a LiveCD for networking.

2) Try running the restricted devices manager, your wireless card may require a restricted driver, which would be listed in the restricted devices manager.

Feisty ships with a utilty called network-manager, which should appear in the system tray as a small monitor-like icon.  Try clicking/right-clicking it for networking configuration.

---

### Post by Gus_T_Reer on 2007-06-26
Ok, I've had a look at the restricted driver manager at it says that the machine doesn't require any restricted drivers.
I've manually configured the network manager to use the wireless network with the appropriate ssid and passkey but there is still no connection. The PCMCIA card looks dead, (no lights), so I suspect that it is not fully installed.

If anyone can give me any further pointers on the way to proceed I'd be grateful.

Thanks

---

