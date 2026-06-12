---
title: "freeze at login"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by unisol on 2007-07-27
i tried adding irqpoll to the /grub/menu.lst, but feisty still freezes up after i login. i guess im going to have to blacklist the rt61 drivers that come with feisty, and install the drivers using ndiswrapper. if that don't work, ill guess ill have to build one from source. does anyone know if  feisty has a module-assistant? thanks in advance.

---

### Post by fredj on 2007-07-27
If you edit the blacklist file in /etc/modprobe.d you can add the driver you don't want to load to this list.
In a terminal type sudo lshw -class network and use the output from that to make sure you have the 
correct full driver name.

---

