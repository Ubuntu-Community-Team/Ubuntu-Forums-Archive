---
title: "How do I search for SSID's?"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2008-04-05
I'm trying to connect to a wireless network for the first time.  Is there a CLI command that I can use to see the SSID's that are broadcast?  Also, is there a program that can find wireless networks that don't broadcast?

Once I find the SSID, how do I connect to the network and input the passphrase?

Is there a way that I can do this in a script?

---

### Post by Tomatz on 2008-04-05
You should be able to l-click on the network applet in the system tray and see available wireless networks. If you can't then it's possible that your wireless card is not supported "out of the box" and you will have to set it up manually.

---

### Post by kevdog on 2008-04-05
iwlist scan at the command line will show you networks that broadcast ssids.  I think you have to use Kismet to find hidden networks.

---

