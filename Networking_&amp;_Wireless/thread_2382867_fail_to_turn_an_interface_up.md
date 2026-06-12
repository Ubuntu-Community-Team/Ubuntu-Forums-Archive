---
title: "fail to turn an interface up"
date: 2018-01-18
forum: Networking &amp; Wireless
---

### Post by jbl92 on 2018-01-18
Hello guys, 

I am trying to configure the wifi on a Orange PI 0 running Ubuntu 16.04.3

Here are the commands I typed : 

 sudo nano /etc/network/interfaces

Then, 

 auto wlan0
 iface wlan0 inet dhcp
 wpa-ssid <My Access Point Name aka SSID>
 wpa-psk <My WPA Password>

finally 
 
 
 sudo ifup wlan0 

and I got the error message : 

  wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
  run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
  Failed to bring up wlan0.

Does someone have an idea on what the problem might come from ? 

Thanks for your help.

---

### Post by jbl92 on 2018-01-18
Problem solved.

---

### Post by QIII on 2018-01-18
Would you care to share your solution with the community so that everyone else can learn, or is everyone else on their own?

---

