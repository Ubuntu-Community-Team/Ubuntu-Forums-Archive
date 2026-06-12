---
title: "Dell Inspiron 1150 wireless not working"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Darkmagic on 2010-10-24
I just installed Ubuntu 10.10 on my Dell Inspiron laptop, but the wireless does not work. Is it that Ubuntu is not detecting my wireless card? 

How do I fix this?

---

### Post by carl.davis on 2010-10-24
Hello

You can check to see if your wireless hardware was properly detected with:

```
sudo lshw -C network
```

I pulled that information from the following page:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

---

### Post by wojox on 2010-10-24
You can also go into Hardware Drivers and see if the driver is there. To download and activate it you'll need your Ethernet cable plugged back in.

---

