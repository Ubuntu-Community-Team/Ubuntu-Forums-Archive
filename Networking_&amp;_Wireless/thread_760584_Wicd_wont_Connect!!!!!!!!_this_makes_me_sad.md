---
title: "Wicd wont Connect!!!!!!!! this makes me sad"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by Greenbean209 on 2008-04-20
So i got Wicd installed and when i start it it doesn't find my wifi or anybodies wifi. i think it might not be connecting to my usb wifi adapter. if it helps you my adapter is a netgear WG111v2. please help :(

---

### Post by kevdog on 2008-04-20
Again the reason for the disconect or lack of connection could be a multitude of issues -- Usually either a poorly configured driver for your device, or something screwed up with the implementation.  To troubleshoot you need to tell us the chipset of your device, the driver you are using, confirm correct installation of the driver, confirm you can "see" your network prior to connection, and then usually connect manually at the command line, just to see if everything works -- and if not -- where in the authentication process is the process hanging.  Usually once all the kinks are worked out, most go back to using network manager or wicd, although many do stick with the command line and access through a script since its the most reliable way to connect.

---

### Post by Whiffle on 2008-04-20
Make sure its set to the corret interface (ie, eth1, ath0, etc), in the Preferences as well.

---

