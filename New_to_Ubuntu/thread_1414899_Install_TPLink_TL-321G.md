---
title: "Install TPLink TL-321G"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Anjriit Id on 2010-02-24
I'm absolutely newbie in linux. i've ubuntu and xp in my pc, but i don't now how to install Driver of my usb wireless TL-321G....????

Anyone can help me..???? Please....


Thanx

---

### Post by cariboo on 2010-02-24
Check dmesg after you have plugged your device in, to see if the device is detected, and if a driver is loaded. To check dmesg go to System-Administration->Log File Viewer, or open a terminal and type:

```
dmesg | tail -n10
```

The above command will print out the last 10 lines of /var/log/dmesg.

---

### Post by 3rdalbum on 2010-02-25
I believe that card should work out-of-the-box on Ubuntu these days. Have you gone to the little network manager icon and clicked it to see if there are networks showing up? The Network Manager icon is a couple of icons to the left of the time/date on the top panel.

---

