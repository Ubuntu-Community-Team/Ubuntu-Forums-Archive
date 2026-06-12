---
title: "Lenovo G-50 Wireless &quot;Greyed out or Not working&quot;"
date: 2015-03-31
forum: Networking &amp; Wireless
---

### Post by Aaron_Hilgart on 2015-03-31
[ATTACH]261003[/ATTACH]

I've tried so many different issues from the fourms. Any personal help would be awesome.

---

### Post by jeremy31 on 2015-03-31
It is just soft blocked so you should be able to enable wifi with the FN+ keyboard combo

---

### Post by Aaron_Hilgart on 2015-03-31
Pressed every Fn combination, nothing turned on. I have laptops bluetooth's off on purpose if thats what you mean.

---

### Post by jeremy31 on 2015-04-01
> **Aaron_Hilgart said:**
> Pressed every Fn combination, nothing turned on. I have laptops bluetooth's off on purpose if thats what you mean.

It was just bluetooth.  I would try setting the country code ```
sudo iw reg set US
``````
gksudo gedit /etc/default/crda
``` The last line should be ```
REGDOMAIN=US
``` Save and exit program

I do remember a hotspot connection causing problems last year, so it might help to delete that with ```
sudo rm /etc/NetworkManager/system-connections/Hotspot
```

Reboot

---

