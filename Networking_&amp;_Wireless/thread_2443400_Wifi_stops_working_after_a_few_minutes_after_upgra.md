---
title: "Wifi stops working after a few minutes after upgrade to 20.04"
date: 2020-05-15
forum: Networking &amp; Wireless
---

### Post by saadmniamatullah on 2020-05-15
Hello. I've been using Ubuntu for quite some time now on my PC (same hardware, no recent updates). I updated to 20.04 a few days ago, and now my Wifi has become very flaky. 

When I boot up Ubuntu, it works fine for a few moments, but then gradually gets more unreliable until it stops working completely. To fix it, I have to open Wifi Settings, and turn off the wifi switch in the status bar, and turn it on again. It works for a few minutes, and then stops until I switch the wifi switch off/on again. I have found that the connection stops working at the exact time when I try to load a page (I have a terminal window pinging 8.8.8.8, and the replies stop exactly when I try to load a page on my browser). After some time not even switching the wifi-button on Settings page will get wifi working again, and I have to restart Ubuntu for it to work. After restarting it works for a while again.

I dual boot Windows 10, which is working flawlessly with the same wifi hardware and on the same network. The previous versions of Ubuntu worked flawlessly. My android phone works flawlessly on the same Wifi network. 

My wireless-info is here: [https://pastebin.com/Wudgyn9Y](https://pastebin.com/Wudgyn9Y)

I couldn't post this from Ubuntu. My wifi was pinging 8.8.8.8 fine until I clicked the "Submit New Thead" button, at which point the wifi stopped working.

Please can anyone help?

---

### Post by phs112 on 2020-06-04
I had the same problem after updating from 18.04 to 20.04. I solved it by switching off the powersaving of the wifi.

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service 
```

---

### Post by nageeb2 on 2020-12-16
Woww finally..Thanks a lot! This solved it for me

---

### Post by thejim on 2020-12-28
nice! this fixed it for me

---

