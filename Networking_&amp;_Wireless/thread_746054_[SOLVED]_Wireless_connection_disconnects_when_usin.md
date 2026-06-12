---
title: "[SOLVED] Wireless connection disconnects when using firefox?"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by Jordy27 on 2008-04-05
I have Ubuntu 7.10 (gutsy) and I am trying to get it working with a wireless usb dongle. So far I have managed to 'connect' using the default rt73usb drivers (it is a Cnet CWD-854 dongle which uses the ralink rt73 chip). When I insert the usb wireless stick, it connects automatically to my home network, and brings up the signal strength bar icon, which shows 4 out of 5 bars. 

However, as soon as I bring up firefox and try to go to a webpage, the wireless connection drops out and I have to restart Ubuntu to get it working again. When it is connected, I can successfully ping my router numerous times. But  if I ping [www.Google.com](www.Google.com), it pings about three times with a value of 220ms and then drops out??

---

### Post by superprash2003 on 2008-04-05
it could be a DNS problem, try changing to open dns server

---

### Post by Jordy27 on 2008-04-06
Hmmm...  I tried that, but to no avail. It may be a little better now - I managed to open one website before wireless cut out, but I think it was just a fluke :(   I have tried updating to 8.04, which will hopefully solve it, but the connection dropped out only seconds into the download.
I have also tried installing different rt73 drivers, however they don't seem to install correctly.

And, as a side issue: when I do manage to connect, my XP laptop connected to the same router sometimes will not connect until I reset the router's starting ip address?

---

### Post by superprash2003 on 2008-04-06
hmm.. you seem to be having a lot of router problems.. you could try resetting your modem and configuring it again.. it might solve all your problems.. have you tried upgrading your router's firmware anytime?

---

### Post by Jordy27 on 2008-04-07
It is now working :)  - Just a case of installing new wireless drivers, as the one that came with Ubuntu was very fickle. For anyone using a wireless device with an rt73 chip that has the same problem, use this howto: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

