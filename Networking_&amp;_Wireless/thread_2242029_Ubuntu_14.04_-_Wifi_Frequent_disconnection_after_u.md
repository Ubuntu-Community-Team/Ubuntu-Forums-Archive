---
title: "Ubuntu 14.04 - Wifi Frequent disconnection after upgrading from 12.04"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by andrebp on 2014-08-30
Hello, 

I upgraded my system from Ubuntu 12.04 to 14.04. With 12.04 my wifi connection was stable, now as long as I actively use the computer it works, but whenever it goes idle (without switching off nor sleeping), wifi does not work anymore. 
I need all the time to disconnect and reconnect using the wifi icon on the top right, then it works. 

I checked online and saw different solutions but was not able to fix it. I paste the script, appreciate if somebody can help, thank you

---

### Post by varunendra on 2014-09-02
Welcome to the forums andrebp !

Please try the fwlps=0 and ips=0 parameters as suggested here : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

Additionally, you should change the encryption type in your router to WPA2-PSK with AES (CCMP). Currently it is using TKIP with WPA2, which is not a standard combination. Reboot the router after saving the change.

If this doesn't help, you may try FreedomBen's customized driver as mentioned in this post by praseodym : [http://ubuntuforums.org/showpost.php?p=13003107](http://ubuntuforums.org/showpost.php?p=13003107) (replace "rtl8188ee" with "rtl8192ce" in the last 'echo....' command). But be aware that many users (within, and outside that thread) have reported kernel panic issues after installing this driver.

I hope setting the parameters with the native drivers, especially ips=0, should solve the problem though and you shouldn't need to try the external driver.

---

