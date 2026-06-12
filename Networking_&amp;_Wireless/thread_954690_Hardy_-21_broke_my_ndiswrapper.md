---
title: "Hardy -21 broke my ndiswrapper"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by TechnoChick on 2008-10-21
A recent Ubuntu upgrade has caused my wireless networking to stop working. I had been using ndiswrapper + bcmwl5 for my Dell Vostro with a Broadcom BCM4328.

I've read in this forum that a linux Broadcom driver is now available and, without reading too closely, see hints that this driver may have become "standard" in the latest Ubuntu upgrade. Is this the "wl" driver shown by lshw -C Network? (see output at bottom of post)

What's the best way to resolve this? I've considered the following:

1) Perhaps if I blacklist wl the original ndiswrapper configuration will continue to work.
2) Or perhaps I simply need to provide WEP configuration information to wl. If so, it is apparently not using the configuration information that shows up in System->Administration->Network Settings.
3) Perhaps I need to disable ndiswrapper (even though it's not running, "lsmod | grep ndis" returns nothing).

I don't know how to do any of those things. Any suggestions or comments would certainly be welcome.

BTW, notice in the output below that the wireless device is wlan0 which I believe is the norm for ndiswrapper. But I have read that the new driver uses eth1. This leads me to believe things are a bit "tangled up".

lshw -C Network
*-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 03
       serial: 00:1e:4c:c0:b2:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

---

### Post by Ayuthia on 2008-10-21
From the information that you posted, your card is trying to use the wl driver.  It can be either eth1 or wlan0.

It looks like all your thoughts are correct.  Like you said, I am not for sure if you need to blacklist ndiswrapper or not since it is currenly not loaded.  I always blacklist the driver just in case.

You might need to enable the wl driver though.  I am not for sure if you have done it yet or not.  You just need to go to System->Administration->Hardware Drivers and enable the Broadcom STA driver.  From there, the wl driver should work.  I cannot remember if the 4328 card and wl driver works with WEP or not though.  You might need to use WPA.

However, if you want to go back to ndiswrapper, you will need to blacklist the wl driver:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

If you want to use the wl driver and blacklist the ndiswrapper:
```
echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist
```

Hope that helps.  If you have more questions, feel free to ask.

---

### Post by TechnoChick on 2008-10-21
Thanks, Ayuthia, for your speedy response! I decided to blacklist wl. This enabled my original ndiswrapper configuration, and my wireless access has been restored.

---
For those who like to experiment, I tried to blacklist ndiswrapper and bcmwl5 in an attempt to get wl to work. That didn't work, so I launched System->Administration->Hardware Drivers. I don't see a reference to "STA". I only have a screen containing two proprietary drivers: the NVIDIA driver needed by my laptop and wl. The status is "in use", but the "enabled" box is not checked. If I attempt to check the box a message appears saying a reboot is required. However, after reboot the box is still not checked enabled.

I'm not going to pursue that experiment because I have been able to successfully restore my orignial wireless configuration using ndiswrapper.

Thanks so much for your help.

---

