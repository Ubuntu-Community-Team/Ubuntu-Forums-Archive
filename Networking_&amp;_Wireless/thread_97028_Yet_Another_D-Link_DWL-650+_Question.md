---
title: "Yet Another D-Link DWL-650+ Question"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by twoseids on 2005-11-30
With Hoary, I had no problem with my wireless card. Could use it at home and in coffee shops. But ever since migrating to Breezy (the first day it was available), I have not been able to use it.

My computer recognizes the card - the problem is that when I try to find available wireless networks (beside "Network Name"), nothing pulls up on the drop-down box.

Any ideas?

---

### Post by Lambert on 2005-11-30
So I take it you have a working driver, you're going into network-admin, choosing the wireless device and clicking on properties. and in the drop down box for essid you don't see anything?

From a terminal can you scan for an ap?

iwlist <wlan0> scan

<wlano> = device logical name

You may need to add sudo to the beginning of the command.

What driver are you using.

---

### Post by twoseids on 2005-12-01
[QUOTE=Lambert]So I take it you have a working driver, you're going into network-admin, choosing the wireless device and clicking on properties. and in the drop down box for essid you don't see anything?

From a terminal can you scan for an ap?

iwlist <wlan0> scan

<wlano> = device logical name

You may need to add sudo to the beginning of the command.

What driver are you using.[/QUOTE]

Yes, you stated my problem correctly. Sorry, I'm kinda new at this...

1. How do I find my device logical name?
2. How do I find out what driver I'm using?

---

### Post by Lambert on 2005-12-01
sudo lshw -businfo

find the class of the device

sudo lshw -C <class>

where <class> is what you found from first command with out the <> in the command

find the configuration: line for the device and it should say driver=xxxx

iwconfig

will tell you device

---

### Post by twoseids on 2005-12-01
Okay, thanks.

1. My driver is acx_pci
2. When I typed  **sudo iwlist IEEE 802.11b+ scan** (did I type the right thing for the device name?), I got this:

```
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
```

---

### Post by Lambert on 2005-12-22
The command for iwlist should have looked more like this.

sudo iwlist eth0 scan
or
sudo iwlist wlan0 scan

801.11b is the protocol for wireless.

Look here for help on the card. 

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

you don't need to build and compile the driver. but go almost half way down the page right after installing driver. There's a small section about firmware and then bringing up the device.

If you're using a lot of hot spots I would suggest looking into 3 apps as many have raved about these making things easier. The gui that comes in breezy is a little buggy. Look into these network-manager; netapplet. These are both in the repositories(network-manager is supposed to be part of the next release) gtkwifi is the third, there's a place for it in the third part projects section of the forums. You may want to try all three and pick the one you like most.

---

### Post by twoseids on 2005-12-22
Thanks a bunch, Lambert - gives me some stuff to work on!

---

