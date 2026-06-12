---
title: "Problems with Wireless Kill Switch"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by howlsmoving on 2008-05-04
I upgraded from 7.10 to 8.04, I am using an intel pro wireless 4965agn wireless card in an hp pavillion dv9000 laptop.  I have no problems connecting to a network after booting, but I like to turn off wifi if I don't plan on using it.  In gutsy as long as I disabled the wireless network from the gnome icon, then flipped off the Wireless kill switch, I could turn it back on and reconnect to the wireless network.  Now, when I do this, I am unable to reconnect to the network.  When I tried this with the gnome applet, dmesg read: [ 6232.557494] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate.  At this point the only way to reconnect to the network is to reboot, but even the process of rebooting doesn't work, I get a green screen with a bunch of illegible messages, so I have to manually turn the computer off.  After rebooting, wireless works fine.


After this, I installed WICD. I turned off wireless, then turned it back on and it said it couldn't find any networks.  At this point ksoftirqd started to use up most of my cpu so I had to restart.  After restarting, wireless works fine.  How can I fix this?

---

### Post by howlsmoving on 2008-05-04
Any ideas?

---

### Post by zdude on 2008-05-04
Have you tried 
sudo /etc/init.d/networking restart

this will stop and restart networking - not pretty but a place to start.

---

### Post by howlsmoving on 2008-05-04
Thanks for responding.  I did try that, and unfortunately it doesn't work.  Anything else to try?

---

### Post by zdude on 2008-05-04
I think there is a bug on this and it is in the driver. You might try installing the hardy-backport. I think this has helped some people.

---

