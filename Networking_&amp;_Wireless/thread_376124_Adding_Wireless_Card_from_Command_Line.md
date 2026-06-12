---
title: "Adding Wireless Card from Command Line"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by zachninme on 2007-03-04
I was setting up my Edgy Ubuntu server when I saw it didn't detect the wireless card. The card works fine under the normal Ubuntu, so it is supported.

I just need to know how I can install it without the GUI I'm used to.

Thanks :D

---

### Post by n00b@linux on 2007-03-05
The (editable) configuration file is /etc/network/interfaces.
The init script is /etc/init.d/networking.
Run the 'ifconfig' command to see all of your network interfaces (wired, wireless and loopback) and you should see your wireless device listed as one of wlan0, eth1, eth2, ra0 or ath0 (it depends on the chipset in your wireless card - I'm presuming it's a PCI device and not PCMCIA/Cardbus nor USB).  If it's not there, it means the kernel module (aka 'device driver') hasn't been loaded.
Run the 'iwconfig' command to check it has been recognised as a *wireless* interface.
Are you using any encryption?

---

### Post by zachninme on 2007-03-05
Its not an interface at all. Its not listed as anything, and thats the problem :-(
(Its PCI)

---

### Post by zachninme on 2007-03-06
Is this just impossible to do?

---

