---
title: "Internet stopped working"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by lzd on 2010-01-31
I uninstalleed Network Manager so I could set up a static IP and everything worked fine for a while but after I restarted the internet stopped working. What do I do?

---

### Post by mikewhatever on 2010-01-31
Which release of Ubuntu are you running? Can you post the output of the following:

cat /etc/network/interfaces

---

### Post by 3rdalbum on 2010-01-31
> **lzd said:**
> I uninstalleed Network Manager so I could set up a static IP

Network Manager is perfectly capable of using a static IP.

Run these commands:

```
sudo dhclient
sudo apt-get install network-manager-gnome
nm-applet
```

The first gets you an internet connection using a dynamic IP, the second gets Network Manager back, the third will run Network Manager applet. Go to the new applet on your panel and right-click it, and then go to Edit Connections. Under "IPv4 Settings" tab, choose Static and set up your static IP address.

---

### Post by lzd on 2010-01-31
Wow, thanks man. That was a lot easier than I expected.

---

