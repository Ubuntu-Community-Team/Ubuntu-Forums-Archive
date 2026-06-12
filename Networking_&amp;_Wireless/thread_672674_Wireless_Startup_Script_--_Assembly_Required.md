---
title: "Wireless Startup Script -- Assembly Required?"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by tim_wright on 2008-01-19
Finally, after much searching, mistakes, tears and yells I finally figured the only way to make macchanger work on my Atheros card. This is the code:

```
sudo wlanconfig ath0 destroy
sudo macchanger --mac=xx:xx:xx:xx:xx:xx wifi0
sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid xxxxxxxxxx key xxxxxxxxxx
sudo dhclient wlan0

```

Can anyone show me how to force this to run IMMEDIATELY after I login. 

Thanks in advance guys :)

---

### Post by kevdog on 2008-01-19
Put those commands (without the sudo) in the /etc/rc.local file -- make the file executable, it will run for all users on boot.

---

### Post by tim_wright on 2008-01-20
Works perfectly! Thank you very much!

---

### Post by kevdog on 2008-01-20
No problem, glad it worked for you!

---

