---
title: "Two wireless network card: How to set priority"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by kenneho on 2013-12-04
Hi all,


I just added an Asus USB-N66 wireless adapter to my laptop, and have now that network card plus the build-in network card. Is there a way to have the network manager prioritize the N66 card whenever it's plugged in? If not I risk having Ubuntu use the built-in network card, even if that one is far worse than the N66 one. 

I'm running Ubuntu 12.04. 


Best regards,
kenneho

---

### Post by varunendra on 2013-12-07
You can 'lock' a connection with the USB adapter by saving the adapter's MAC ID in Network Manager settings' "Device MAC address" field. If the device is not plugged in, you can change this setting back to the available device's MAC address (if it doesn't change back automatically, I'm not sure if it will).

You'll have to disconnect --> reconnect after changing this.

If you need a full automation, I don't know of a decent way other than creating a somewhat messy script and associate it with a 'udev' rule (which I haven't done before, but am quite sure it'll work).

---

