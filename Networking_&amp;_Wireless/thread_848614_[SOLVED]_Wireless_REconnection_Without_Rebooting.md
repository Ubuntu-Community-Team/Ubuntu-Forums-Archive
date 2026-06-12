---
title: "[SOLVED] Wireless REconnection Without Rebooting"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-07-03
Occasionally, my home wireless connection drops. I have tried several combinations of stopping KNetworkManager and re-running the network scripts, but I ultimately have to reboot. I don't mind restarting the wireless; I just want to avoid rebooting each time.

Here's my /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

I would prefer to avoid manual configuration, if possible.

Any ideas on how to solve this? That is how to I shutdown everything and then restart, as if I had rebooted?

tnx
cmn

---

### Post by jimv on 2008-07-03
sudo /etc/init.d/networking restart

doesn't help?

---

### Post by cmnorton on 2008-07-03
Thanks for the answer. That is the first thing I tried, and it does not help.

---

### Post by cmnorton on 2008-07-11
I don't know why this is fixed, but I forgot to turn on the T61's radio switch when I logged in from home. I turned on the switch and then connected to my wireless network even though none were listed. The next time I logged in, I connected immediately to my wireless network.

---

