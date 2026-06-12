---
title: "No Wireless Option"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by nikolardo on 2008-11-21
Ok, so I'm running 8.10, from a clean install.
It says under Restricted Hardware Drivers that the driver for my Atheros wireless (it's built in, and I don't have a wireless switch) is activated and in use.  That may be true.
However, when I right-click the Network Manager Applet, there is only one checkbox; Enable Networking.
There should be a checkbox that says "Enable Wireless."
There isn't.
I'd really like my wireless to work, can anyone help me out?
Oh, by the way, the wireless isn't working.

---

### Post by unix192 on 2008-11-21
right-click the Network Manager Applet and click on edit connections, in there is a wireless tab where you can add your wireless network settings. worked for me

---

### Post by nikolardo on 2008-11-21
tried it, entered all the right things
still didn't work
is there any way i can get my network manager to say the right things?

---

### Post by unix192 on 2008-11-22
Try this

[http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup](http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup)

---

### Post by nikolardo on 2008-11-25
tried it, had actually tried it beforehand...
still doesn't work
sorry, the problems i get are usually pretty stubborn

---

### Post by nvance on 2008-11-25
Greetings,

Make sure that you have the Intrepid backports installed (available via the Synaptic Manager) and then reboot.  Once you have rebooted, take a look to see if the option is available for you to use the wireless.  I had the same issue with my laptop but no drivers were even showing up therefore I had to blacklist my Ath05 to get the wireless working.

Hopefully that will help out with your issue.

---

### Post by nikolardo on 2009-03-26
got around it by using Ndiswrapper and the appropriate driver.

---

### Post by cableguyxx on 2009-08-01
> **nvance said:**
> Greetings,

Make sure that you have the Intrepid backports installed (available via the Synaptic Manager) and then reboot.  Once you have rebooted, take a look to see if the option is available for you to use the wireless.  I had the same issue with my laptop but no drivers were even showing up therefore I had to blacklist my Ath05 to get the wireless working.

Hopefully that will help out with your issue.I just wanted to thank you for your help on this issue.  I recently bought a new HP laptop with the Atheros card, and couldn't get it to recognize, but adding the Intrepid backports and restarting fixed it immediately:D .

---

