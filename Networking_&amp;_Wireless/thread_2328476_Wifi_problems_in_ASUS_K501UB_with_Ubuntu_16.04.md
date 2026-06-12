---
title: "Wifi problems in ASUS K501UB with Ubuntu 16.04"
date: 2016-06-21
forum: Networking &amp; Wireless
---

### Post by pablo51 on 2016-06-21
I am having problems with the Wifi connection in my laptop ASUS K501UB. When I go to System settings inside of  Network holder, the Wireless is always in OFF and I can not turn it ON. I do not have problems using wired connection (LAN). Can you help me please?
Thanks in advance,
Pablo

---

### Post by X-RED_Tech on 2016-06-21
There's a specific section here for networking and wireless issues. It's called [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336"). :)
There you can find this sticky thread: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

With the wired connection follow the above instructions and post the results of the script.We need to know what hardware you have as this [specs page]("https://www.asus.com/Notebooks/K501UB/specifications/") doesn't help much. We need to know what *[COLOR=#333333][FONT=Segoe UI]Integrated 802.11 b/g/n or 802.11 ac (On selected models)[/FONT][/COLOR]*[COLOR=#333333][FONT=Segoe UI] actually is.[/FONT][/COLOR]*[COLOR=#333333][FONT=Segoe UI][/FONT][/COLOR]*

---

### Post by DuckHook on 2016-06-21
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by jeremy31 on 2016-06-21
First check ```
lsmod | grep asus
```
If the results show asus-nb-wmi, then do
```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```

reboot

---

### Post by pablo51 on 2016-06-23
> **jeremy31 said:**
> First check ```
lsmod | grep asus
```
If the results show asus-nb-wmi, then do
```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```

reboot


Thanks a lot Jeremy31, it works perfectly.....  :D:D:D
Pablo

---

### Post by jamjar919 on 2016-08-31
> **jeremy31 said:**
> First check ```
lsmod | grep asus
```
If the results show asus-nb-wmi, then do
```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```

reboot

Fixed for me on a brand new install on brand new laptop as well - Thankyou very much!

---

### Post by visualblind on 2017-01-07
Awesome worked great on my Asus K501UW with Ubuntu 16.04.1 LTS 4.4.0-57-generic :) Thanks for posting the resolution.

> **jeremy31 said:**
> First check ```
lsmod | grep asus
```
If the results show asus-nb-wmi, then do
```
echo "options asus-nb-wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb-wmi.conf
```

reboot

---

