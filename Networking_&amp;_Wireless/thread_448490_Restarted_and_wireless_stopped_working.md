---
title: "Restarted and wireless stopped working"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by Ryanson on 2007-05-19
I apologize if this has been posted before, but I couldn't find it anywhere.

I have a Toshiba Satellite p105-s9337 with integrated Intel wireless. I had some trouble getting it connected, but after fooling around for a bit, it started going. A while later I restarted the computer, and now the wireless won't work. In network manager, my wireless connection is gone (only the wired one shows up). I checked restricted drivers and it says the wireless driver is enabled but not in use. I tried to toggle it to in use, but to no avail. I've had linux for a while now, but this is the first laptop I've tried it on, and I am still quite the newbie. Any help would be much appreciated.

Thanks

---

### Post by chili555 on 2007-05-19
How about opening a terminal and showing us:```
sudo cat /var/log/messages | grep Kill
```Sometimes, when formerly working perfectly wireless just doesn't work, the wireless switch has been nudged to 'off.' 

You might also do:```
sudo cat /var/log/messages | grep 3945
```See if there are any error or suspicious messages.

---

