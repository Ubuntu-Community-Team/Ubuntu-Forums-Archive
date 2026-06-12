---
title: "Internet connection has stopped working."
date: 2016-02-03
forum: Networking &amp; Wireless
---

### Post by gregory21 on 2016-02-03
I'm running Ubuntu 14.04, and my internet connection has completely stopped working. There is no connections menu in settings, and even with an ethernet cable plugged in, my computer refuses to connect. Anybody know what the problem is?

---

### Post by cariboo on 2016-02-04
You are quite short on information, what did you do before networking stopped. Telling us what hardware and driver your system uses would help. Run the following command, and paste the output in your next post:

```
sudo lshw -C network
```

You could also try:

```
sudo service NetworkManager restart
```

---

