---
title: "Asus X541UAK.202, Ubuntu 16.04 wireless wifi keeps disconnecting"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by ckrac on 2017-11-18
Hi, I installed ubuntu about a week ago and the wifi keeps dropping randomly. It would sometimes prompt me that wifi got disconnected and it would reconnect with itself. I mostly have to reconnect the wifi manually myself every 3mins or so and at times it would remain connected for about 20mins. The icon in the corner will show me as connected even when I am disconnected. Other laptops are connected to the same wifi and have no connections issue. 

Here is the wireless info script: [http://paste.ubuntu.com/25991818/plain/](http://paste.ubuntu.com/25991818/plain/)
[COLOR=#000000]
[/COLOR][COLOR=#000000]
Thank you for any help you can give me.[/COLOR]

---

### Post by ckrac on 2017-11-22
[COLOR=#000000]I searched posts with similar problems with realtek adapter (rtl8821ae) and tried some suggestions. None of them worked.

[/COLOR][COLOR=#000000]Here is what I tried:

[/COLOR]
[COLOR=#000000][FONT=&quot]sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]systemctl restart network-manager.service[/FONT][/COLOR]

[FONT=&quot]sudo apt-get install linux-headers-generic build-essential git 

git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)

cd rtlwifi_new

make

sudo make install[/FONT]

[FONT=&quot]sudo modprobe rtl8821ae[/FONT]

[FONT=&quot]sudo modprobe -r rtl8821ae[/FONT]
[FONT=&quot]sudo modprobe rtl8821ae[/FONT]

[FONT=&quot]sudo modprobe -r rtl8821ae[/FONT]
[FONT=&quot]sudo modprobe rtl8821ae ant_sel=1[/FONT]

[FONT=&quot]sudo modprobe -r rtl8821ae[/FONT]
[FONT=&quot]sudo modprobe rtl8821ae ant_sel=2[/FONT]

---

