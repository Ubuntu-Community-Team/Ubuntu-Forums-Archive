---
title: "Create Virtual SSID"
date: 2020-05-12
forum: Networking &amp; Wireless
---

### Post by tbastian on 2020-05-12
I'm trying to set up a virtual test environment, and the code I'm testing relies on a) a network interface named wlan0, b) a specific SSID + credentials. Using VirtualBox, is there any way I can fake this? I figured out that with a bit of config file (/etc/udev/rules.d/70-persistent-net.rules) magic I can name the device anything I like, but the SSID has become a show-stopper.

If it makes a difference, I'm running 16.04.

---

### Post by CelticWarrior on 2020-05-12
For something like this you'd need to have a hardware WiFi dongle or card assigned exclusively to the VM. The virtualized network device can't be used, it's for all intended purposes an Ethernet device so no SSIDs involved.

---

### Post by tbastian on 2020-05-12
Thank you for the response CelticWarrior. I'll talk to the developer, see if we can mock some of this stuff up in code instead.

---

