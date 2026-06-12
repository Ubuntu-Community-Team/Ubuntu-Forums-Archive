---
title: "WUSB54GC + Feisty Fawn"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by njdfan1241 on 2007-07-26
Hey everybody..i'm havin a problem. My linksys wusb54gc is detected along with my network, but when I try and connect those two dots just swirl and nothing happens...any ideas?

---

### Post by njdfan1241 on 2007-07-26
come on people...nothing?

---

### Post by kevdog on 2007-07-26
You will need to tell us the chipset of the device.  I believe it is a ra2500 but I could be wrong.  Take the information you have, type at command line

```
lsusb
```

And then taking these two pieces of info, google around until you can discover the chipset.  Until we know this critical piece of information, Im afraid I cant provide you much help!

---

### Post by njdfan1241 on 2007-07-27
Ok, I tried this guide:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

The driver loaded fine and did

i```
isudo ifconfig wlan0 up
sudo iwconfig wlan0 essid mynetwork
sudo iwconfig wlan0 key "off"
sudo dhclient wlan0
```

And it doesn't connect...I type sudo dhclient wlan0 and it tries but doesnt succeed. It try's to connect to 255.255.255.255, shouldnt it connect to 192.168.1.1?

---

### Post by ayenack on 2007-07-27
You may want to take a look at [this]("https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC"). Also as kevdog said it might be an idea to show the results of lsusb in terminal which should give you the model number and chip type.

Best of luck.

Have you got WEP or WPA enabled on your router?

---

### Post by njdfan1241 on 2007-07-27
> **ayenack said:**
> You may want to take a look at [this]("https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC"). Also as kevdog said it might be an idea to show the results of lsusb in terminal which should give you the model number and chip type.

Best of luck.

Have you got WEP or WPA enabled on your router?

Ok i'll look into that...and No, thats why I typed "off" for the key

edit: I just notcied something..when i did dhclient it said it was trying to connect to 255.255.255.255 (or something like that)
but my routers subnet mask is 255.255.255.0....anyway I can change where dhclient tries to connect to?

---

### Post by hendricks on 2007-08-03
Hey guys, I've made a script that will make this work in Ubuntu/Kubuntu Feisty. Please check it out at this thread:

[http://ubuntuforums.org/showthread.php?p=3127959#post3127959]("http://ubuntuforums.org/showthread.php?p=3127959#post3127959")

It worked for njdfan and myself. Let me know how it goes.

  --Hendricks

---

