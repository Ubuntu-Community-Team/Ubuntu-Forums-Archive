---
title: "Help Setting Up Internet !!!"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Roeyfreak10 on 2008-06-11
just got linux on my computer. im now dual-booting xp and linux 8.04. i have a wireless network adapter, it is a linksys wireless usb network adapter (wusb11 version 2.6). When i go to the top and click the networks button it shows my internet so i click it and it says im connected and it has a 45% connection but when i go to any website it doesnt work. please help i really need to be able to go on the internet.


ok for cat /etc/resolv.conf 
i get...

search chn.comcast.net
nameserver 192.168.0.1

and for iwconfig
iget...

lo no wireless extension
eth0 no wireless extension
wlan0 ieee 802.11b essid:wireless internetz nickname:
mode:managed frquency:2.437GHz access point:00:0F:66:65:E0:13
bit rate:11/mbs tx power=15 dbm
retry limit=8
rts thr=1536 b
fragment thr=1536 b 
power managment = off
link quality = 30/100
signal level = 30/100

---

### Post by ugm6hr on 2008-06-11
Give some more detail: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

Also - out put from:
```
route -n
```

And what happens when you go to here: [http://66.249.91.104/](http://66.249.91.104/)

---

### Post by Milardo on 2008-06-11
I would try this-using hardy,open synaptic manager and make sure you check the cd option so it can install stuff from cd, search for ndis and install all those ndis that come up in the search. After installing them in adminstration go to windows wireless drivers. Have your 3 or 2 files from the linksys cd or the one from linksys website. The .cat, .sys, and .inf files. Install new driver the .inf file and next go to the top right icon that looks like a computer monitor. Right click the iconand make sure network and wireless are checked. Next left click it and click the option that is search or find new wireless network not the create or manual option. Now you can enter your wireless security settings and you can easily choose wpa/wpa 2 as well. It should connect pretty fast. I got high speeds as well. To disconnect and unplug adapter (if that is what you have) just uncheck wireless from the icon and then pull out the adapter. To connect to the same wireless network you just have to plug it back in and check wireless if not already checked. You should be connected in about 50 seconds or so. This worked for my linksys wusb54gc.

---

### Post by superprash2003 on 2008-06-11
try changing DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

