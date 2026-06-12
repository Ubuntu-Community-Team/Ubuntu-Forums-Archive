---
title: "Unstable wireless network"
date: 2016-02-04
forum: Networking &amp; Wireless
---

### Post by dragonator2 on 2016-02-04
Hello,

I have just installed Ubuntu on my new laptop and my wireless network appears to be really unstable. I don't think it's from the router. I even disabled wireless N, but it still persists. I was thinking maybe I should update the driver, but I don't know exactly how to do that.

This seems to happen when I am downloading large files, even from computers on my local network.

I have attached the results of the wireless info script.

Please help if you can. Thank you in advance.

---

### Post by jeremy31 on 2016-02-04
If you can change wireless encryption settings on the wireless router, change it to WPA2 only as it shows WPA version 1 used along with WPA2

---

### Post by dragonator2 on 2016-02-05
The network I'm using is DragonationLink. The only option I have is for WPA/WPA2 Personal, Enterprise or WEP.

---

### Post by jeremy31 on 2016-02-05
The settings in the router, not in Ubuntu Network Manager

---

### Post by dragonator2 on 2016-02-05
Yes. I'm using a TP-LINK TL-WDR4300 with the latest stock firmware. I do not have that option on the router.

---

### Post by dragonator2 on 2016-02-05
I think I may have identified the root cause: this only appears to happen when using a bluetooth mouse. The connection to the mouse is equally unstable. Maybe the signals are interfering with each other?

---

### Post by jeremy31 on 2016-02-05
If it is a bluetooth coexistence issue, this may help ```
echo "options ath9k btcoex_enable=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot

---

### Post by dragonator2 on 2016-02-08
Thank you, but unfortunately it seems that didn't work. Pinging google has fewer dropped packets but I have up to over 3000ms ping. As soon as I disable bluetooth it drops to 15ms.

---

### Post by jeremy31 on 2016-02-08
I would experiment with different channels on the router, it is possible bluetooth may have less interference if wifi is on channel 13

---

### Post by dragonator2 on 2016-02-14
This didn't happen on Windows as far as I could tell. Can't test now because I wiped it and went full ubuntu + virtualbox.

In any case, I ordered a new mouse that's not on bluetooth.

Thanks for all the help.

---

