---
title: "Load all wireless networks"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by sorfrena on 2008-07-15
Hi all

I am enjoying ubuntu 7.10
sometimes it happens it just don't shows allo wireless netwrorks available...I have to wait too long for the right connection show up, or even reboot (but I can assure the connection is present).
Is there any method to force ubuntu to show up all wireless networks in range?

Thank you all

---

### Post by jingo811 on 2008-07-15
Maybe typing this in terminal will show you all routers.
```
iwlist wlan0 scan
```
Then do this to connect to a router.
```
iwconfig wlan0 essid Some_Name
```

---

### Post by Arthur Archnix on 2008-07-15
This is simply a bug in network manager. I used to see this all the time until I stopped using it. Now that I use wpa_supplicant to connect to my wireless networks I have not seen a network disappear once. 

For most people though, I'd recommend staying with network manager or upgrading to a newer version of Ubuntu to get newer versions of your wireless driver and network manager, both of which ought to improve your experience. Until the next version (Ibex) comes out, however, you may wish to experiment with simply reloading network-manager as opposed to restarting your computer. 

Something along the lines of killall nm-applet and then nm-applet --disable might be what you're looking for. 

Hopefully others will chime in with the correct way to do this, as I unfortunately cannot experiment and give you more precise instructions.

---

