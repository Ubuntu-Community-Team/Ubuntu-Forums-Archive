---
title: "Mildly experienced, no device name"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by calderra on 2007-04-13
I have a slight idea of what I'm trying to do here, but Linux documentation always frustrates me for some reason, so I'd appreciate any human support. Using 6.06 "Dapper".

My wireless connection isn't in networking, so I followed the online troubleshooter and ran 'lshw -businfo' trying to find my wireless connection:

(example, my ethernet connection shows up like...)
bla@xx  eth0  bridge  [driver]
(and my wireless shows more like)
bla@xx  (no eth#) (something  that's not a bridge) [driver]

So I've got a type, driver, and bus info, but it hasn't been assigned an eth#? Also, the driver info actually matches (to the letter) the way that Windows describes my wireless, so I imagine that part's fine. So... err... what do I do to actually make it USE the driver? Troubleshooting seemed to want to move to modprobe next, but without the eth#, I don't think there's any mods to probe. Heh.

---

### Post by chili555 on 2007-04-13
You are getting close! Unfortunately, the information you omitted is the information we need the most! Please do:```
sudo lshw -C network
```Skip the wired interface and post everything you can after *product:* and *configuration:* about the wireless. We will get it going.

---

### Post by calderra on 2007-04-13
I have no components under the "network" category. My ethernet is "communications" and my wireless is "generic". So I ran lshw -C generic instead to get:

usb: 1 UNCLAIMED
description: Generic USB device
product: USB Wireless 802.11b/g adaptor
vendor: Gemtek
physical id: 8
bus: usb@1:8
version: 0.01
capabilities: usb-2.00
config: maxpower=300mA speed=480.0mb/s

---

### Post by chili555 on 2007-04-13
Which model of Gemtek USB is it? WL-what? That will help us a great deal.

---

### Post by calderra on 2007-04-13
Wow this is getting messed up... here's some fun:
So lsmod says that my device has been successfully detected as a standard USB wireless, but lshw's configuration line does not list a driver, which is why it's missing from the above post. From the troubleshooting page, I think I know exactly what boat I'm in:

[snip]
TODO: describe what it means when it shows *-network UNCLAIMED, and no configuration line is
present.
[/snip]

I have a configuration line, but it only shows what I listed- no driver information is present.
:confused: 

Aaaaannnnyway... trying to find the exact model of my Gemtek is proving to be a bother. This PC was a bargain with my significant other ("let's just buy one so we know it works". heh.) which means it's still under warranty, so cracking the case is something I'd rather avoid at the moment. Theoretically I should have more than enough info to find the device, but I still can't narrow down specifics.

Computer: HP Pavillion Slimline s7700n
Driver name: netr73.sys, provided by Ralink
And anything I try to download relative to drivers from Gemtek always seems to load a generic driver for all similar devices.

But if Gemtek's website info is still accurate for my device, the only possible model they list that matches me is the WPI-100G. And from other lookups, that makes it a BroadCom chipset.

EDIT: And I tried another thread where a user said he was in a similar situation, and to use lspci to see if the device is indeed listed as broadcom- tried lspci and lsusb, and didn't see the device in either list.

---

