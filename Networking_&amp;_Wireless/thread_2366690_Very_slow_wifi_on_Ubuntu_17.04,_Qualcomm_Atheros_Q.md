---
title: "Very slow wifi on Ubuntu 17.04, Qualcomm Atheros QCA6174"
date: 2017-07-20
forum: Networking &amp; Wireless
---

### Post by distancy on 2017-07-20
Hi, I'm experiencing very slow wifi on my laptop. Right now using Google's speed test I'm at 0.4 Mbps download / 1.1 up. On my phone, on the same wifi network in the same physical location, I get 3.9/5.7. 

I haven't experienced this before. I'm visiting a friend so I'm on a Wifi network that I've never used before, but even yesterday, while it was slow, it wasn't nearly this bad. (I didn't run a speed test yesterday so I can't compare quantitatively.)

I ran the script from [this thread]("https://ubuntuforums.org/showthread.php?t=370108") and [here is the output]("http://paste.ubuntu.com/25134850/").

Any help would be much appreciated.

Thanks!

---

### Post by jeremy31 on 2017-07-20
Lets see if it as easy as disabling wireless power management
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```

---

