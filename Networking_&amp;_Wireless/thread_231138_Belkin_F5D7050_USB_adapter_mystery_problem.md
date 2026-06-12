---
title: "Belkin F5D7050 USB adapter: mystery problem"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by zytsef on 2006-08-07
I'm a first time Ubuntu user attempting to get a Belkin USB wireless adapter working.  Initially, after installation, it seemed to be detected correctly. however I was unable to get an IPv4 address after I configured the essid and key.  I have since tried the RT2500 USB source from [Ralink]("http://www.ralinktech.com/supp-1.htm") and also the rt2570 driver from [the rt2x00 Open Source Project]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads").  Think the problem is the adapter is unable to connect to the AP for some reason.  It is configured correctly, but no connection.  iwconfig shows no AP MAC address, not even all zeros like if it just simply wasn't connecting.

Here's the output for lsusb:
```

Bus 004 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi

```

Any ideas as to what the problem is?

update: I can now get connected to the AP with the driver Ubuntu tries first, but it's still not assigning an IP.

update 2: I managed to get the default driver working with the network config tool after it froze the system a couple of times.  Everything is working fine now.  Thanks for checking.

---

### Post by alecjw on 2006-08-08
The reason for it not working is that Belkin drivers are non-open source, meaning that the drivers can't be used in linux. There are about 5 belkin network cards which work with ubuntu, none of which are usb adapters. Even therese drivers had to be remade for linux.

---

### Post by zytsef on 2006-08-08
On the contrary, if you go to the rt2x00 open source project I linked to in the first post you'll see this particular adapter listed as supported.  In fact, after looking into it further, I believe ubuntu uses that very driver.

The constant freezing whenever I try to change the configuration through the graphical panel is a bit of a pain, though.  Bug reported.

---

