---
title: "WiFi with Realtek 8187b"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Amallric on 2008-08-17
Hello,

I am a newbie in the world of Linux, I just installed Ubuntu yesterday. Like many other users I have a problem with the wireless card Realtek 8187b. I know there are plenty of posts about this here, but I didn't manage to found a thread describing exactly the same problem as mine. 

So, there is some information:
-using Ubuntu 8.04 Hardy Heron

-wireless card driver: the Windows XP driver downloaded from the realtek website and installed with ndiswrapper. Seems to work fine, the device is recongnized and listed in the Network Manager as well as in the ndiswrapper GUI.

-Connection: does not work. In the roaming mode, no wireless networks are available; in the manual mode my attempts to connect failed.

-I tried to use wpa_supplicant as advised but when I type the instruction in the terminal nothing happens! :confused: I am not experienced with Linux maybe its normal but it does still not make the connection work.
I type something like this:
```
sudo wpa_supplicant -c/etc/wpa_supplicant.conf -Dndiswrapper -iwlan0 start
```

wpa_supplicant.conf is configured as advised in one of the tutorials I found. 
wlan0 is recongnized as a wireless interface. So what's wrong?

Sorry for my bad english :( and thanks.

---

