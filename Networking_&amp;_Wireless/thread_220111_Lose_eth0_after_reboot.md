---
title: "Lose eth0 after reboot"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Dragonmantank on 2006-07-21
I'm trying to set up Ubuntu Server 6.06 under ESX server, and I'm trying to get the VMXNet (gigabit ethernet) driver to work with eth0. ESX is all set up, and if I do a 'modprobe vmxnet', 'ifconfig eth0 up' it will work until I reboot.

I changed /etc/modules.conf to 'alias eth0 vmxnet' but that doesn't seem to have cleared up the problem. The driver and everything works great, but after any reboot I have to modprobe again. 

What else should I check?

---

