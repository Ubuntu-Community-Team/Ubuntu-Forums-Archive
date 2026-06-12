---
title: "Unable to Install Tatadocomo 3G on Ubuntu"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by bhoopendra.cisco on 2013-12-18
Hello Team,

I'm Using Ubuntu 12.04.3 LTS. I'm unable to Install the TataPhoton 3G(GSM), apparently the OS has no problem in detecting the Photon+(CDMA) and it is working without any issue. Kindly help.

---

### Post by varunendra on 2013-12-21
Welcome to the forums Bhoopendra !

Open a terminal (Ctrl-Alt-T) > unplug the Photon 3g dongle > wait about 20 seconds > replug the dongle > wait another 10-20 seconds, and enter the following commands in the terminal -
```
uname -mr
lsusb
dmesg | tail -20
```
..and post back their outputs here.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by vipinhari on 2014-02-23
Try using sakis3g to connect. Check this link for details [http://askubuntu.com/questions/406975/tata-docomo-3g-dongle-in-linux-mint-or-ubuntu/423768#423768](http://askubuntu.com/questions/406975/tata-docomo-3g-dongle-in-linux-mint-or-ubuntu/423768#423768)

---

