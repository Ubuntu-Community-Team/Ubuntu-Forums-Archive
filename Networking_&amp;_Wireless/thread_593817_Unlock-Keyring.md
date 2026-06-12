---
title: "Unlock-Keyring"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by AndyPopely on 2007-10-27
If like me you'd rather not have to enter a password to unlock the keyring for NetworkManager when your wireless adapter tries to connect the network .. try WICD.   

Your router needs to broadcast the SSID but if you're using wep/wpa etc
that shouldn't be a problem.

Here's what I did:-

  1) download wicd_1.3.4-all.deb to the desktop from
       [https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)
       don't install it yet
  2) open a terminal window
  3) sudo apt-get remove network-manager
  4) sudo apt-get autoremove
  5) ignore popups from the NetworkManager applet about not finding resources ... they will stop
  6) close the terminal window
  7) double click wicd_1.3.4-all.deb on the desktop to install it
  8) when finished installing open system -> preferences -> sessions
  9) uncheck Network Manager
10) press +add
11) enter wicd in the name field
12) enter /opt/wicd/tray.py in the command field
13) close the sessions window
14) open applications -> internet -> wicd
15) press the arrow against the network you want to connect to
16) check automatically connect to this network if that's what you want to happen on every boot
17) click on advanced settings
18) check use encrption if you're using wep/wpa etc and make approriate changes
19) press preferences and check that wireless interface states what you use wlan0, ath0 etc
20) when done click connect against your network
21) reboot to make sure your wireless connection works

---

### Post by Trapper Dave on 2008-02-15
That works a treat, thank you.

---

### Post by staama on 2008-03-16
Works like a charme, it didn't take more than 10-15 min. to install and setup WICD.
Thanks a lot!

---

