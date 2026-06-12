---
title: "Wifi not working on laptop model 17-X115DX"
date: 2016-12-23
forum: Networking &amp; Wireless
---

### Post by brandan13 on 2016-12-23
I'm using lubuntu 16.04. The wifi was worked on windows 10. In the lubundu indicator applet network menu (I think that's what it's called), It says that the wifi is disabled. I tried enabling it. It didn't working. It wasn't working the lubuntu usb os either.

Some Debug: [https://hastebin.com/sufizoyeke.pas](https://hastebin.com/sufizoyeke.pas)
Here's the link to the irc logs. I'm LiftLeft. Maybe that will be useful. [https://irclogs.ubuntu.com/2016/12/23/%23ubuntu.html](https://irclogs.ubuntu.com/2016/12/23/%23ubuntu.html)


Really Weird Thing (This happened about an hour after I posted this): I just to happen to have a realtek 802.11n wlan usb adapter. Which works. But that's not the weird part. This happened once. I can't seem to repeat it. I connected the usb adapter to the wifi router. I then was able to connect the wifi card to the router. I rebooted. I now can't connect the wifi card to the router. The wifi card shows up in the indicator applet when I have the usb adapter, but it doesn't show any networks.

---

### Post by jeremy31 on 2016-12-23
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Reboot and the block should be gone

---

### Post by brandan13 on 2016-12-23
ok that worked, thanks

---

### Post by prashant-bhatia on 2016-12-31
Hello,

I am pretty new to Ubuntu and need some assistance in enabling my wifi  on my HP Pavilion X360 Laptop. I have installed Ubuntu 16.04 alongside windows  10 but on a different partition.

Pls find the results of the script mentioned here -  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)

Would really appreciate some assistance. I have already tried the trick  to remove and reinsert battery but that hasn't helped either.

---

### Post by jeremy31 on 2016-12-31
The linked page contains the script itself not the output from the wireless-info.**txt** file

Please start your own thread with the wireless-into.txt file results

---

