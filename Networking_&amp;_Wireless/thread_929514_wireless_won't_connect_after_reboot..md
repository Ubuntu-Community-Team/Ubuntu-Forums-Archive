---
title: "wireless won't connect after reboot."
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by tacticalbread on 2008-09-25
my wireless net refuses to connect after I reboot my PC. I was connected, and I rebooted, and I couldn't connect. I somehow got connected again, rebooted again, and now I can't connect. It keeps telling me "Attempting to join the wireless network." and then it will ask me for the WEP key again. I put it in, (I know it's the correct key), and it attempts again, but then it will ask me again for the key. The same thing happens forever, no matter how many times I put in the key, or manually connect or whatever.

---

### Post by tacticalbread on 2008-09-25
it connects fine when connecting to an unencrypted connection, but any connection with security on it, I can't connect. And I know I am putting in the correct WEP key.

---

### Post by lisati on 2008-09-25
If you're being asked for a password each time you might find this link helpful: [http://ubuntuforums.org/showthread.php?t=463621](http://ubuntuforums.org/showthread.php?t=463621)

If, however, you have no signs of networking after a restart or reboot, you might find this helpful: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

### Post by tacticalbread on 2008-09-25
Network Manager asks me for my WEP key, and when I put it in, it attempts to connect, but won't, and asks me for the key again. This happens no matter how many times I put the key in, and I know I'm putting in the correct key.

---

### Post by willca on 2008-09-26
try this way

edit /etc/network/interfaces

This is assuming you are using dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid whateveritis
wireless-key whatkeyitis

Save and restart networking.
sudo /etc/init.d/networking restart

---

