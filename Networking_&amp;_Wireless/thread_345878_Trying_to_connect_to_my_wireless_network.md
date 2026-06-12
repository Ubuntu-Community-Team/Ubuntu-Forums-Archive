---
title: "Trying to connect to my wireless network"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Gladjaframpf on 2007-01-24
I just got Ubuntu 6.06 running on my second computer and I'm trying to get it connected to the network so I can access the Internet. I have a D-Link DWL-G122 USB Wireless Adapter and I'm trying to connect to a DI-524 Wireless Router. 

I set everything up in the Networking manager, but it still didn't work. Then I tried [this guide]("https://help.ubuntu.com/community/WifiDocs/WiFiWithSomeoneElsesRouter"), and it seemed to be working up until I tried to set the encryption key, at which point I got an "Unknown Error 524".

Does anyone have any idea what my problem might be, or anything else I could try?

---

### Post by almax00 on 2007-01-25
is encryption and/or MAC address filtering enabled via the router? check the configuration of your router via the other computer and turn all encryption/security off. and try turning the router off for 30 seconds then back on after making the above changes...sometimes a power cycle can help.

did you use ndiswrapper to install the windows drivers? i did a google for your error and found a post that mentioned uninstalling ndiswrapper or blacklisting the ubuntu native driver -- blacklisting worked. if you want to take a look:
[http://www.ubuntuforums.org/archive/index.php/t-189146.html](http://www.ubuntuforums.org/archive/index.php/t-189146.html)

good luck.

---

