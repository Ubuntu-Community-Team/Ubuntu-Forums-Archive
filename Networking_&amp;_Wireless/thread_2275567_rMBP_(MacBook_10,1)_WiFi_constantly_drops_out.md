---
title: "rMBP (MacBook 10,1) WiFi constantly drops out"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by zach32 on 2015-04-27
Hello,

I recently installed Ubuntu 14.04 on my rMBP (MacBook 10,1) and at first getting the WiFi set up was impossible. I have no option to use Ethernet in my living situation and Ubuntu wouldn't recognize my WiFi hardware so after searching for a long time I found the drivers on my OS X partition and transferred them to my Ubuntu install via a USB drive and installed them.

Running `lshw` gives me this output for networking:
```

*-network       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: b8:f6:b1:19:72:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.16.0-30-generic firmware=666.2 link=yes multicast=yes wireless=IEEE 802.11bg

```

So as you can see, I have the `b43` driver installed and I can finally connect to the internet! However, every 2 minutes or so my connection drops out and I need to wait for it to give me internet access again, and when I do have internet it is much slower than on OS X.

If you have any advice on what I can try to fix this I would greatly appreciate it!

---

