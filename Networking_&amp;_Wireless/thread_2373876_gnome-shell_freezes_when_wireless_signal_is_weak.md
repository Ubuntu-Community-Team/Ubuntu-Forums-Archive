---
title: "gnome-shell freezes when wireless signal is weak"
date: 2017-10-10
forum: Networking &amp; Wireless
---

### Post by aeronutt on 2017-10-10
Quite frustrating!

Whenever the wireless connection is weak/flaky, gnome-shell freezes for 15-30 seconds,and repeats every few minutes until I locate a stronger Wifi signal. Also, if there's ANY issue with wireless connecting (say a router problem), gnome-shell freezes for 15-30 seconds, and repeats every few minutes.

Dell 5510 Precision laptop.
Network controller: Qualcomm Atheros QCA6174
Ubuntu 17.04

Should I switch to wicd or such? Any nm settings I can post/change/debug?

Thanks!

---

### Post by praseodym on 2017-10-10
There is a bug in 17.04 and the NWM. Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by aeronutt on 2017-10-10
Thanks!!   I'll give this a shot and report back.

---

### Post by aeronutt on 2017-10-11
UPDATE: The above edits helped tremendously. Although gnome-shell sometimes still 'pauses' for a second or 3 when the wifi signal is weak, it's MUCH improved. Very usable now.

Is this bug/issue fixed in 17.10?

I'll mark as solved, THANKS!

---

### Post by praseodym on 2017-10-11
Don't know if it fixed in 17-10, however, it did not appear in 16-04 LTS ;)

---

### Post by aeronutt on 2017-10-11
Yea, I never had a problem with 16.04LTS on my previous (old) laptop, but 16.04 had serious problems on my new 5510, hence the move to 17.04.
All is pretty good now.

---

