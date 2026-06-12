---
title: "Reconnecting to a network"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by AlexanderPetros on 2007-09-05
I have an Windows XP machine hooked up to my apartment's internet connection, and I my Ubuntu machine is hooked up to the XP one by a crossover cable to get internet. If I have to restart the Windows XP computer the Ubuntu machine won't reconnect to the internet without a reset. There's a popup message saying its connected to the network again, but I still have no internet connection. How can I manually tell it to reconnect to the internet?

Thanks.

---

### Post by kevdog on 2007-09-05
Perhaps try:

sudo /etc/init.d/networking restart

or 
sudo /etc/init.d/dbus restart

or 
sudo ifconfig <interface name> down
sudo killall dhclient dhclient3
suod ifconfig <interface name> up
sudo dhclient <interface name>

---

