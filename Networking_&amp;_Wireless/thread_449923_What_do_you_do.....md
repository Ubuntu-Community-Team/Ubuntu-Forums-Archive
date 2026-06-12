---
title: "What do you do...."
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by J44053 on 2007-05-20
I have an ECS 536 laptop with a built in wireless card.  Under the network manager menu I see a list of SSIDs, but I cannot connect to any of them.  Under the Device manager I have an Rt2500 802.11g Cardbus mini PCI wireless card adapter thing. What do I do to get it to work.

---

### Post by daller on 2007-05-21
Just to make sure that the driver for the card is initiated, please run this command from a terminal:

gksudo modprobe rt2500

---

### Post by J44053 on 2007-05-21
What is supposed to happen?  I did what you said and I got nothing.  Anything else I could try?

---

### Post by daller on 2007-05-22
If you run the command, you'll just get a blank line!

Like this:

daniel@daniel-laptop:~$ sudo modprobe rt2500
daniel@daniel-laptop:~$

Have you tried to get the network running after this?

---

### Post by J44053 on 2007-05-23
gksudo and sudo commands didn't work.  Anything else I could do?

---

### Post by J44053 on 2007-05-24
It didn't work.

---

### Post by ugm6hr on 2007-05-24
> **J44053 said:**
> I have an ECS 536 laptop with a built in wireless card.  Under the network manager menu I see a list of SSIDs, but I cannot connect to any of them.  Under the Device manager I have an Rt2500 802.11g Cardbus mini PCI wireless card adapter thing. What do I do to get it to work.

What happens when you click on one of the SSIDs?  And is your network's SSID displayed?  What security do you use on your network?

PS: I suspect the driver is working if you get a list of SSIDs.

---

### Post by J44053 on 2007-05-25
When I click on an SSID I get a prompt for my network key.  It's WEP encryption.  It tries to connect and even right in front of the router nothing happens.

---

### Post by ugm6hr on 2007-05-26
I'd recommend you use the HEX WEP key (rather than Passcode / ASCII).  If you are already doing that, or it doesn't work - do you have MAC filtering on?  Might be worth turning off all security briefly to try and make sure it can connect - then you can sort the security out after.

---

### Post by J44053 on 2007-06-06
Now I get a connection status bar with about 70%, but no websites will work? I am extremely confused.

---

