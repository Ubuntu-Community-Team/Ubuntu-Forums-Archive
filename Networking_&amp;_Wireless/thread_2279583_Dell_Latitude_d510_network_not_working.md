---
title: "Dell Latitude d510 network not working"
date: 2015-05-24
forum: Networking &amp; Wireless
---

### Post by Zeitung on 2015-05-24
Hi, Im quite new to Ubuntu, so please be patient.

So, yesterday I installed Lubuntu 15.04 to my Dell latitude d510 laptop. Wifi didn't work from the start so I started to look for solution. I used this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29) sites b43 info: 
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

Then I rebooted laptop and after that wifi was still not working.

```
ifconfig wlan0 up
```
"No such device"

wifi controller: bcm4318 [14e4:4318]

e: "Software & Updates"> Additional Drivers : there "Using broadcom 802.11 Linux STA driver wireless driver source from bcmwl-kernel.." is enabled(blue spot).

Thank you for ur help!

---

### Post by chili555 on 2015-05-24
For your benefit and the benefit of the searchers, the stickie here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)  says that the proper package is not the STA driver, so please do:```
sudo apt-get purge bcmwl-kernel-source
```And then install the correct package:```
sudo apt-get install firmware-b43-installer
```And then reboot.

---

