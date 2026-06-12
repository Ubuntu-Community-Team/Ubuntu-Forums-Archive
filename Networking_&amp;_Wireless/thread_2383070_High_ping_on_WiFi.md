---
title: "High ping on WiFi"
date: 2018-01-20
forum: Networking &amp; Wireless
---

### Post by jiaman on 2018-01-20
SSH has some high input lag (e.g. typing, takes some ms before it appears on screen, enough to notice an issue). On my VPSes, and other PCs this doesn't persist. When I ping it's local address, they're abnormally high (>100, vs <10 on other devices). 

iwconfig gives this, 
```
Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0
```

According to other posts, it's apparently a power management issue? I ```
sudo iwconfig wlp58s0 power off
```, disabled it and it was resolved. Is this the proper way of dealing with this? What are the consequences of this? This isn't permanent either, how would I go about making it do it automatically when rebooted?

---

### Post by jiaman on 2018-01-20
According to this [https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on](https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on), it's a bug.

This can be resolved by adding the following to /etc/network/interfaces.
```
post-up iwconfig wlan0 power off
```

---

### Post by jeremy31 on 2018-01-20
I would just do the following in Ubuntu 16.04 and newer
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

Actually a bug report was filed on the way it used to be [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1557026](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1557026)

---

