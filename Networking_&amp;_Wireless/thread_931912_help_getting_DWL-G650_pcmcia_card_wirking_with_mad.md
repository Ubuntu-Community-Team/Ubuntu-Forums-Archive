---
title: "help getting DWL-G650 pcmcia card wirking with madwifi driver"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by chex_m8 on 2008-09-27
I need help getting this DWL-G650 PCMCIA card working in ubuntu. I want to use madwifi driver not ndiswrapper. please help walk me through this. I've already installed the madwifi driver but card still doesn't work. thanks

---

### Post by sanicki on 2008-11-10
1. Install MadWifi:
sudo apt-get install linux-restricted-modules madwifi-tools
2. Reboot:
sudo shutdown -r now
3. Configure:
sudo nano /etc/network/interfaces
(add this...)
auto ath0
iface ath0 inet dhcp
5. Restart Networking:
sudo /etc/init.d/networking restart

Hope that helps.

---

### Post by jcs1 on 2008-11-10
> **sanicki said:**
> 1. Install MadWifi:
sudo apt-get install linux-restricted-modules madwifi-tools
2. Reboot:
sudo shutdown -r now
3. Configure:
sudo nano /etc/network/interfaces
(add this...)
auto ath0
iface ath0 inet dhcp
5. Restart Networking:
sudo /etc/init.d/networking restart

Hope that helps.

Being new to Ubuntu and having the same problem with a DWL-G650 Version 4.31 card I tried to run this command. The following error messages appeared:"r [from -r] not known". When I ran only the sudo apt-get... command line the message "could not find package"came up. 
Help would be much appreciated. Thank you!

---

