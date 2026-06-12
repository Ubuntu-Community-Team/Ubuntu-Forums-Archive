---
title: "Modprobe -r rt2800pci and then reload fixes my problem"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2016-10-16
I'm having wireless problems when I switched up to 16.04. I've looked through the forums and tried many different things, but finally discovered that removing and then running the driver for my wireless card would fix the problem.

I've been trying to figure out how to get this not to occur when rebooting - where should I start looking. I'm currently running egrep looking for rt2800pci on my harddrive. I know that I created an interface file under /etc/network but that's just to help sign on from my headless server to my wireless router.

Where else should I be looking for changes to networking? How can I fix this so that a reboot does not break wireless again without running modprobe?

---

### Post by jeremy31 on 2016-10-16
Check ```
iwconfig
``` to see if power management is on before or after removing and modprobing the module

This should fix the power management re-enabling
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 0/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

