---
title: "Wired network &quot;device unmanaged&quot;"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by b-boy on 2008-10-07
Hi guys i have done a network manager update today and after i rebooted I cannot connect to a network via eth0 when i click on the network manager icon its says WIRED NETWORK *device unmanaged*my wireless network is fine 


please help

---

### Post by DamianC on 2008-10-07
Hi, I had exactly the same issue here, and you cant manually edit any of the settings within network manager as saving fails.

I temporarily sorted it by killing the network manager and starting the networking manually.

#sudo /etc/init.d/networking stop
#ps aux | grep Net

root      6220  0.0  0.1   6400  2252 ?        Ss   12:13   0:00 /usr/sbin/NetworkManager
root      7078  0.0  0.1   7696  3508 ?        S    12:17   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf

#sudo kill -9 6220 7078
#sudo /etc/init.d/networking start

as long as your /etc/networking/interfaces file is correct then this should get you back online.

I didn't try it yet, but if you apt-get remove network manager or just remove it from startup this should stop it from taking over again if you have to reboot your computer.

I love it when stuff like this happens. I'll just keep checking for another NetworkManager update.

---

### Post by b-boy on 2008-10-07
thanks for the help

---

