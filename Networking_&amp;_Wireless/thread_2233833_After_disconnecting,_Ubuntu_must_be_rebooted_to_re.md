---
title: "After disconnecting, Ubuntu must be rebooted to reconnect to wifi"
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by hfinger on 2014-07-11
[TABLE]
[TR]
[TD="class: votecell"]     0     down vote          [favorite]("http://askubuntu.com/questions/496315/after-deliberately-disconnecting-ubuntu-must-be-rebooted-to-reconnect-to-wifi#")          [/TD]
[TD="class: postcell"]                I had to disconnect from the Netgear CG3100D wifi router for  maintenance work, but when I chose [wifiLogo] > defaultAccessPoint,  an authentication dialogue appeared. After typing the correct key,  Ubuntu 12.04 LTS would not reconnect. But when I shut down and restart,  Ubuntu reconnects normally. Why does it seem to ignore the  authentication?
  On Windows 7 Professional, reconnection occurs automatically.
      
[/TD]
[/TR]
[/TABLE]

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep "Eth\|Net" -A2

---

### Post by varunendra on 2014-07-13
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

