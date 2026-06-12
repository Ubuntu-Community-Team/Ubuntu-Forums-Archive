---
title: "Wlan connection dies out"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by grav on 2008-01-03
I have setup a Zydas ZD1201 wlan usb stick according to [another post]("http://ubuntuforums.org/showpost.php?p=2031024&postcount=10"), and got the wlan connection up and running with no problems.

However, the connection dies out if there is no network traffic for a while.

When it goes down, I can get it up and running by doing

```
sudo /etc/init.d/networking restart

```

and I can keep the connection alive by constantly pinging the router, so it's nothing critical, but is it possible to debug the connection in any way?

Regards,
Mikkel

---

