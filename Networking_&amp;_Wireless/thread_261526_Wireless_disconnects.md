---
title: "Wireless disconnects"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by bastiegast on 2006-09-20
I got my rt2560 wireless card (finally) working. I configured it using wireless tools but somehow i had to reconfigure it everytime i rebooted so i created some sort of script for it:
```
ifconfig wlan0 down
iwconfig wlan0 mode Managed
iwconfig wlan0 key open xxxxxxxxxx
iwconfig wlan0 essid xxxxxxxxxx
ifconfig wlan0 up
dhclient wlan0
```
Fortunatly after a little playing with /etc/network/interfaces i could get wireless working from bootup. But heres the problem: after a while, wireless gets disconnected, probably because our wireless modem sucks and the connectoion is poor, it happens in windoze all the time. But everytime wireless gets disconnected i have to restart networking (/etc/init.d/networking restart) or run the script above. In windows, the computer just keeps trying to connect if wireless gets disconnected but in ubuntu it wont, so how can i automate this?

---

### Post by bastiegast on 2006-09-22
Well since nobody yet replied, i helped myself :) Network manager did not not work for me somehow, so i went in synaptic and downloaded every wireless managemnt app you can think of, they all did not work(dont recognize wlan or couldnt connect) except for netapplet :) love it, it allows me to connect and reconnect without root privileges

---

