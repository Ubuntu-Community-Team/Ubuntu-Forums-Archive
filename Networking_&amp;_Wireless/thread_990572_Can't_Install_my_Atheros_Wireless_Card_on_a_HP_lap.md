---
title: "Can't Install my Atheros Wireless Card on a HP laptop"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by nukker009 on 2008-11-22
I just changed to Ubuntu today :grin:. Everything has been going smoothly so far ,but I just can't install my wireless card.
Anyone knows how I can make it work or a direction to another thread? 
I really appreciate you help :).

---

### Post by mdhunn on 2008-11-22
I had the same problem with my HP G60.  You can get a driver that works here:

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

I tried using a driver from HP's website using ndiswrapper. That was a mistake.  Now I don't have wifi till I load the correct driver using a script after I log in.  It works but I would rather have it loaded as the computer boots up.  Any help with that would be appreciated.  Here is the script that I use:

cd /home/mark/wirelessDriver/compat-wireless-2008-11-21/
sudo make unload
sudo modprobe ath9k

If you have to use a script to load the driver:
Do not just copy and paste my script!  It uses make unload in the directroy where I built the driver and loads the driver for my machine into the kernel!  Be sure to read the info at Linux Wireless before you do anything.

Update:
appended ath9k to /etc/modules Works like a charm :) Just be sure that you use the right module.

---

### Post by Olivier2371 on 2008-11-22
Here are two links that you can have a look at.

[http://linuxwireless.org/en/users/Drivers/ath5k]("http://linuxwireless.org/en/users/Drivers/ath5k")
[http://linuxwireless.org/en/users/Drivers/ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k")

---

