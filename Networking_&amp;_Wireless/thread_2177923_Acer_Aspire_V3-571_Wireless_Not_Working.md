---
title: "Acer Aspire V3-571 Wireless Not Working"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by mxermadman on 2013-10-01
Hi, folks.

I'm new to Ubuntu. I've just installed it on my Acer Aspire V3 laptop. It's working great but the WiFi doesn't work at all. Can anyone point me in the right direction to getting it up and running?

Thanks much.

---

### Post by MIJ-VI on 2013-10-01
Hi.

1) Which version of Ubuntu are you using?

2) Please run [SIZE=1][FONT=courier new]sudo lshw[/FONT][/SIZE] in Terminal and then post the results here within CODE (#) tags so that others can see which WiFi card etc your notebook uses.

3) If it uses a WiFi card made by Broadcom, then you'll have to install its driver & firmware from the Ubuntu repositories via a wired Internet connection. How this is done varies slightly from one version of Ubuntu to the next.

---

### Post by varunendra on 2013-10-02
Welcome to the forums mxermadman ! :)

To answer precisely what MIJ-VI asked, and a little more, please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use code tags (please follow the "Using Code Tags" link in my signature to see how). Thanks.

**PS:**
> **MIJ-VI said:**
> How this is done varies slightly from one version of Ubuntu to the next.
Not really. It differs depending on the variation of the card (b43-lpphy, b43legacy or plain b43 firmware), not the OS version. :)

Apart from individual commands for each, there exists a common package which installs all the firmware in one go - linux-firmware-nonfree. To install it -
```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by mxermadman on 2013-10-03
Hey guys, thanks for the help. I ran the install linux-firmware-nonfree, and rebooted, no dice.

Here is my output.

Thanks again!

```

Ubuntu 12.10
3.5.0-41-generic i686
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3
--
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Foxconn International, Inc. Device [105b:e04b]


```

---

### Post by varunendra on 2013-10-03
That's because the firmware is for b43 driver, and b43 does not support you card -
```
03:00.0 Network controller [0280]: Broadcom Corporation **BCM43228** 802.11a/b/g/n [**14e4:4359**]
```

Your card is supported only by the proprietary sta driver. To install it (while you are connected by other means) -
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Watch out for errors, post back if there is any (there shouldn't be any though). If all went smooth, you should have a working wifi.

---

### Post by mxermadman on 2013-10-03
It worked! Thank you, I now have functioning wifi.

However, during that last install, errors did pop up:

```
DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules


```

I'm just curious what's going on there. But my WiFi is indeed working.

Thanks again.

---

### Post by varunendra on 2013-10-04
You're welcome ! :)
> **mxermadman said:**
> However, during that last install, errors did pop up:

```
DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules

```

I'm just curious what's going on there. But my WiFi is indeed working.

Interesting indeed. Those should have been just notifications or at most warnings, not errors.

When the sta driver is installed, it blacklists all the above drivers so as to avoid possible conflict over resources. While doing so, it **checks** if any of them is loaded and unloads it if found loaded.

The messages above are from this very same stage (checking and unloading if found loaded). Since your card is not supported by any of the above drivers, they were not found in the /proc/modules (which is where loaded modules are listed). So it should have been just a notification which is like telling us - "this module is not loaded, so nothing to do here..". Never noticed these messages before, so not sure if it is a (harmless) coding mistake or if I was just ignorant all this while.

In any case, the above (if it is all that it says) messages are harmless and shouldn't have any side effects. But thanks for the heads up !

Hope the driver plays well with your card. :)

---

