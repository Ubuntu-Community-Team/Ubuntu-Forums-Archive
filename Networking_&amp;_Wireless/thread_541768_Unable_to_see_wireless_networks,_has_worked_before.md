---
title: "Unable to see wireless networks, has worked before"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by frankjr on 2007-09-03
Hello, I've been using the bcmwl5.inf with ndiswrapper for a few days now, and I've been able to have wireless networks show up in the nm-applet panel and be able to connect to them, until recently. Now, no wireless networks show up, no matter how many times I have tried to reinstall them. The wlan0 interface still shows up, but I am not able to connect to anything, even manually.

---

### Post by Kobalt on 2007-09-03
Hello,

What do you get when you run this ```
iwlist wlan0 scan
```

---

### Post by frankjr on 2007-09-03
No scan results...

---

### Post by Kobalt on 2007-09-03
Then I think you should try to reinstall both ndiswrapper and the driver.

---

