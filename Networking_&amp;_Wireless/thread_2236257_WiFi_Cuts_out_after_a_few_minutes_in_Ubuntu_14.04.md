---
title: "WiFi Cuts out after a few minutes in Ubuntu 14.04"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by ogburn-joshua on 2014-07-25
I have an HP Pavilion 23 something or other and my Wifi Will work for a few minutes and then all of the sudden it just stops and my wireless network no longer appears in the wifi list in the menu. The network powers all my other devices with no problem. I thought it might have been a result of my tinkering with Ubuntu (as i am new to Linux) So i just completely erased my hard drive and reinstalled it but it still has the same problem. I had a dual boot with windows (which is now erased) but on the windows side it worked fine, so im guessing this has somthing to do with driver support but not sure. Im a complete newbie so could somebody give me a hand with this..its pretty annoying to have to keep reseting my computer just to surf the web. Thanks!

---

### Post by jeremy31 on 2014-07-25
To get some info about your hardware and settings, open a terminal window CTRL+ALT+t and enter this ```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
``` and attach the resulting wireless-info file in your next post

---

