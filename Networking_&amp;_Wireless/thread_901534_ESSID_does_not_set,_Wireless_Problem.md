---
title: "ESSID does not set, Wireless Problem"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by MikeRaines on 2008-08-26
Hey,

I am having an interesting problem. My weireless was working fine all summer, but now that I have come back to school it is no longer responding.

iwlist wlan0 scan scans available networks correctly. I can see both my personal router and the University public wireless. But when I attempt to connect to them it always fails.

The script I am using for wireless is:
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid "UA Public Wireless Network"
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo dhclient wlan0

```
The strange thing I noticed when this started happening was that even manually setting the essid from command line fails. Network manager is not running I do all my networking on the comand line.
```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 "Any Essid"

```
Does not work.

If I run sudo iwconfig wlan0 after setting the essid it still lists as ESSID:off/any

This has had me netless for about 2 weeks now. Any helps would be greatly appreciated.

---

