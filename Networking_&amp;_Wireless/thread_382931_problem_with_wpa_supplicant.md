---
title: "problem with wpa_supplicant"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Griffiss on 2007-03-12
After following this howto:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)


I inptu:```
sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w
```

which causes this to happen:```
Trying to associate with 00:0f:b5:18:d7:4a (SSID='Myssid' freq=2462MHz
Association request to the driver failed
WPA: Failed to set PTK to the driver.
Associated with 00:0f:b5:18:d7:4a
#then repeates the last two lines until I hit Ctrl+C whereupon:#
CTRL-EVENT-TERMINATING - signal 2 received
Failed to disable WPA in the driver.
```

Can anybody tell me what this means and how to resolve it please?



*Resolved now thanks to:*

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

