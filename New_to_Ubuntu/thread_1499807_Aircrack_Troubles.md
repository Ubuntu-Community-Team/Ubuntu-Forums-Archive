---
title: "Aircrack Troubles"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Hastor on 2010-06-02
I recently downloaded aircrack, but when I attempted to pull the interface up with 

```
sudo airodump-ng eth1
``` 

I get the message "ioctl(SIOCGIFINDEX) failed: No such device". I have no clue why this is 

happening and am a bit worried over the state of my wireless card. If my wireless card is 

in working order shouldn't it just work out? Any help would be appreciated. Thanks.

---

### Post by uRock on 2010-06-02
Reading this may help. [http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

---

### Post by darkdragn on 2010-06-02
The interface name, eth1 tells me it's an ethernet device... so, airodump shouldn't work on it (Not to mention, with it being eth1 it's telling me that you have 2 ethernet interfaces installed... which you probably don't). What kind of wireless card are you working with, because your wireless interface should be something along the lines of wifi0, wlan0, or ath0. Something similar to that. Have your wireless drivers been patched to support packet injection?(Since that may cause issues further down the road) Have your ran airmon-ng start $WirelessInterface ( example is "airmon-ng start wifi0") to put an interface in monitor mode?

I'm sorry if i sound a little mean, just some things to look at/questions i have about the issue. Let me know, and i'll try helping out as much as i can.

---

