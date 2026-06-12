---
title: "Noob broke it... Wifi"
date: 2017-08-07
forum: Networking &amp; Wireless
---

### Post by caseytc on 2017-08-07
SO i was following a older [tread]("https://ubuntuforums.org/showthread.php?t=2304607") on the Weak realtek wifi and after a reboot the card no longer shows up.

TO give a background this is a newer HP nootbook that sucked with windows 10 so i am trying out Linux. im not sure how to fix but im sure if i reinstall i will work again just dont want to. need to fix this lol

ubuntu 16.04
yes is was a rtl8723be

nothing important on the laptop

---

### Post by caseytc on 2017-08-07
[http://paste.ubuntu.com/25266536/](http://paste.ubuntu.com/25266536/)

---

### Post by wildmanne39 on 2017-08-07
Please try:
```
sudo modprobe rtl8723be
```
if it does not come on you will need to post exactly what you did because that is a long thread and you could have done everything in it.

Thanks

---

### Post by caseytc on 2017-08-07
well i just reinstalled quickly and it works again. sadly the wi-fi only works upto 10 feet away from the router but it works.

---

### Post by wildmanne39 on 2017-08-07
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

