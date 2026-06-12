---
title: "WIFI signal is very weak on HP laptop RTL8723BE (Tried so many solutions)"
date: 2018-12-26
forum: Networking &amp; Wireless
---

### Post by razz47 on 2018-12-26
Greetings everyone,


I have tried every solution I could find as there are a lot out there with the same issue but still can't get a strong wifi signal. I'm using an HP laptop with a RTL8723BE wireless network adapter on Ubuntu 18.04.1 LTS. 


I was able to resolve this issue in the past (not long ago maybe a month or so) by downloading and following the steps here at [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) , but now it's not being fixed anymore.


When I run iwlist scan | egrep -i 'ssid|quality' I get very close results for both antennas (ant_sel=1 or ant_sel=2) always -70 or less.


I read somewhere that the new kernel has fixed this issue, so I updated my kernel but couldn't get it fixed yet.

Please let me know what to do to help you help me :) 


Any help is appreciated!

---

### Post by chili555 on 2018-12-26
Please run and post:```
uname -r
nmcli dev wifi list
```Thanks.

---

