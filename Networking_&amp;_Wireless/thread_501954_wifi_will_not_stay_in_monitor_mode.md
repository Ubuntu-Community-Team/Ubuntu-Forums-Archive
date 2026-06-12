---
title: "wifi will not stay in monitor mode"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by justind on 2007-07-16
I have a linksys wmp54g and when I put it into monitor mode it will only stay in for a little bit then I have to put in the command again. Is there some way to lock it into monitor mode? 
BTW I am using this to put it into monitor mode:
```
sudo iwconfig ra0 mode monitor
```

Thanks in advance

---

### Post by justind on 2007-07-16
bump

---

### Post by MyR on 2007-07-16
The network manager takes the card out of monitor mode after a certain amount of time. If you don't want it to do this, right click on it's icon in the task tray and uncheck "enable networking". Perhaps you can just uncheck "enable wireless", I haven't tryed it.
peace

---

### Post by justind on 2007-07-16
Ok, thanks I'll try that.

---

