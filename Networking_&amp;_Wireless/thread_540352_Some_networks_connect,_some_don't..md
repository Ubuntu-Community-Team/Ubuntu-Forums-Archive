---
title: "Some networks connect, some don't."
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by rollerskatejamms on 2007-09-01
Strangely enough the networks that work BEST for me are WPA networks.
With WEP networks, or no encryption/password networks, I usually have to use iwconfig to connect.

For example at school, I'll see the "b@ruchwir3l3ss" network. When I tell nm-applet to connect to it, it just goes on and on forever and doesn't work.

However if I drop to a terminal, and do the following:
```
sudo iwconfig eth1 essid "b@ruchwir3l3ss"
sudo dhclient eth1
```

That works just fine. Any idea how I can get nm-applet to connect?

I mean personally fine I can drop to the terminal, but we can't expect non-geeks to have to know to do sudo iwconfig eth1 essid "b@aruchwir3l3ss" && sudo dhclient eth1. :confused:

---

### Post by Zorael on 2007-09-01
I recommend [wicd](http://wicd.sourceforge.net), it seems to drive home everytime NetworkManager falls short. I just wish it'd be added to the official repositories. :)

---

### Post by rollerskatejamms on 2007-09-01
Can wicd handle wpa?

---

### Post by imdano on 2007-09-03
Yes, it can.

---

### Post by rollerskatejamms on 2007-09-03
I tried wicd, but its a bit buggy and it removed nm-applet when you install it. I do like it though.

---

