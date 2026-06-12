---
title: "Slow Wifi"
date: 2019-01-26
forum: Networking &amp; Wireless
---

### Post by boucherja4784 on 2019-01-26
Hey everyone new to Ubuntu and the forum.  I've tried researching this issue but from posts I've seen the resolutions have been pretty specific to each user's machine.  I tried following a post to disable powersave mode on the NetworkManager bu that didn't speen up my WiFi.  Any help would be greatly appreciated.

[http://paste.ubuntu.com/p/CyMzT4WmQ2/](http://paste.ubuntu.com/p/CyMzT4WmQ2/)

---

### Post by praseodym on 2019-01-26
2,4 GHZ region shows 13 channels, however, it shows time zone US. Is that right? If yes, run
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot. You may also try
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by boucherja4784 on 2019-01-26
Thanks for the reply, but that didn't seem to change anything.  I am connected to the 5 GHz so the 2.4 GHZ region shouldn't affect things I wouldn't think.  Either way I tried both commands and am still getting download speeds of about 6 MBPS when I'm getting about 180 MBPS on another machine.

---

### Post by boucherja4784 on 2019-01-26
Here is my wireless-info after performing those commands.

[http://paste.ubuntu.com/p/hRBRHTNs3s/](http://paste.ubuntu.com/p/hRBRHTNs3s/)

---

### Post by boucherja4784 on 2019-01-26
Here is my wireless-info after performing those commands.

[http://paste.ubuntu.com/p/hRBRHTNs3s/](http://paste.ubuntu.com/p/hRBRHTNs3s/)

---

### Post by boucherja4784 on 2019-01-26
So I found another post that recommended updating the kernel version. 

[https://askubuntu.com/questions/1067205/ubuntu-18-04-1-lts-intel-wireless-is-very-slow-with-kernel-4-15](https://askubuntu.com/questions/1067205/ubuntu-18-04-1-lts-intel-wireless-is-very-slow-with-kernel-4-15)

I updated my kernel from 4.15 to 4.20 but no difference in performance was found.

[http://paste.ubuntu.com/p/tdYhqSxvRc/](http://paste.ubuntu.com/p/tdYhqSxvRc/)

---

### Post by boucherja4784 on 2019-01-26
So another update.  I switched to using the 2.4 GHz band on my router and now I"m getting 60 MBPS.  Not sure why that makes a difference.  Also, not sure why I'm still getting such a difference from my other machine that's getting 180 MBPS.

---

### Post by boucherja4784 on 2019-01-31
So I got the Ubuntu kernel update today and that solved the issue.

---

