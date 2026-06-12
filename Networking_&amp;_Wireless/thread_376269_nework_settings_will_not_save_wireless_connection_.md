---
title: "nework settings will not save wireless connection settings"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by david2m3h on 2007-03-04
I installed nd1211 driver for my belkin wireless g usb dongle (model F5d7050) on 6.11 kernel. It works fine except every time I reboot I have to run the following command before my wireless works

*sudo dhclient eth1*

I tried to configure my wireless connection in **System -->Administration-->Networking** but it will not save my wireless connection settings. It will save the changes I make to my wired connection just fine, but every time I change my wireless connection settings it reverts back to what it was when I first installed the nd1211 driver as soon as I close the network settings manager.

I am guessing that these two issues are related, I am not sure. What I would like is for my wireless connection to work on boot without have to run any manual commands each time.

---

### Post by gradedcheese on 2007-03-04
That's strange.  I assume you're not using NetworkManager, right?  You can manually write the settings in /etc/network/interfaces (which is what the Networking took modifies).  Post the contents of that file here please.

---

