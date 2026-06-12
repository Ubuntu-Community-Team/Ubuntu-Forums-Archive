---
title: "Feisty auto ifup/ifdown issues."
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Austin_KW on 2007-05-27
I have a wireless network pcmcia and a usb card that are not network manager aware. Or rather the network manager is not aware of them. So I manually configure via /etc/network/interfaces

On edgy when I removed the card, an ifdown would automatically run. So when I reinserted the card it would auto ifup and connect. 

In feisty when I remove the card,  /var/run/network/ifstate still reflects that adapter as configured so I have to manually run "sudo ifdown" before reinserting the adapter. I was using this 'feature' to repair my connections when the had probems and lost connection.

How can I reenable this functionality?

---

