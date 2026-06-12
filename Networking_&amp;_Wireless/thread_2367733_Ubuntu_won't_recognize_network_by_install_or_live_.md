---
title: "Ubuntu won't recognize network by install or live usb; OSX is fine."
date: 2017-08-02
forum: Networking &amp; Wireless
---

### Post by finny388 on 2017-08-02
Xubuntu 14.04 on an iMac dualbooting with OSX. Wireless stopped on July 25.

In troubleshooting I tried reinstalling the broadcom drivers (after power cycling and recreating the wifi profile). 

Then I tried a distro (kde neon) booting from live usb. No wifi.
Boot into OSX and wifi works.

Setup is:
Wireles Router/Modem (WRM) wired to Apple Airport
OSX connects via wifi to Airport
Xubuntu previously connected via wifi to Airport

If you request me to go to terminal let me know xubuntu or live usb.

So wierd, i will try with ethernet to complete the broadcom drivers tonight

---

### Post by finny388 on 2017-08-03
I ended up using Ethernet and installing Ubuntu mate 16.04.
No wifi
Tried to install broadcom from additional drivers and it said the "device not working" and wouldn't apply.

Tried from command line and now wifi works just fine.

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by finny388 on 2017-08-03
I was replying on mobile and couldn`t find the mark solved function.
Anyway, done.

---

