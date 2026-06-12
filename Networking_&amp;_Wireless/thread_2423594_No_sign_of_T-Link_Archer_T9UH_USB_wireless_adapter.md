---
title: "No sign of T-Link Archer T9UH USB wireless adapter on Ubuntu 18.04.2 LTS"
date: 2019-07-25
forum: Networking &amp; Wireless
---

### Post by ipman228 on 2019-07-25
Hi,
This is the first time I'm posting on a forum as I usually get my answers by looking at other people's posts. I am new to linux and am in over my head. I installed Ubuntu and all is fine except that my wifi adapter is nowhere to be seen! I've tried a whole host of possible solutions and it made no difference. I really don't want to go back to windows but it seems like the only option at this point. I foolishly decided to start doing all of this while I have 3 assignments due for university so this has been stressing me out very much. I've attempted to install the drivers: rtl8814au and rtl8812au in many different ways to no avail.

Here is my paste bin: [URL="http://paste.ubuntu.com/p/bT6fCKpC4x/"]http://paste.ubuntu.com/p/bT6fCKpC4x/
[/URL]
When I run dmesg:

[ 1297.717849] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[ 1297.866220] usb 1-1: New USB device found, idVendor=2357, idProduct=0106, bcdDevice= 0.00
[ 1297.866226] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1297.866230] usb 1-1: Product: 802.11ac NIC
[ 1297.866234] usb 1-1: Manufacturer: Realtek
[ 1297.866237] usb 1-1: SerialNumber: 123456

These are the last couple of lines. Is this referring to my adapter??

I apologize if I made any annoying mistakes in this post. I read the sticky thread beforehand and tried to follow it as best I could. Thank you in advance.

UPDATE:
The pastebin from above is from a new install, after realizing that I hadnt downloaded the drivers in the new ubuntu install I followed:

[https://askubuntu.com/questions/1057730/how-to-compile-tp-link-t9uh-wireless-driver-without-internet-access-im-running](https://askubuntu.com/questions/1057730/how-to-compile-tp-link-t9uh-wireless-driver-without-internet-access-im-running)

And now everything is working somehow.

However, the command "lsusb" still does not seem to show the connection with my adapter:

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1532:002e Razer USA, Ltd RZ01-0058 Gaming Mouse [Naga]
Bus 001 Device 004: ID 0c45:7603 Microdia 
Bus 001 Device 002: ID 2357:0106  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Anyone have any idea why?

---

### Post by jeremy31 on 2019-07-26
The USB device info comes from a online database, your device might be in the newer version, do ```
sudo update-usbids && lsusb
```
See if it shows anything different

---

### Post by chili555 on 2019-07-26
> 
However, the command "lsusb" still does not seem to show the connection with my adapter:
lsusb will always show what is encoded in the hardware as the description. In your case:```

Bus 001 Device 002: ID 2357:0106 

```Nothing at all shows nor will ever show because TP-Link didn't encode the desciption in the hardware for lsusb to read. The presence or absence of a driver, the author of the driver, etc. can never change this. 

However, the description is for human consumption only. It makes no difference at all to the system. The system reads the usb.id, namely 2357:0106 and finds that it does or does not have an appropriate driver. We know that your system does now have a driver because:> 
And now everything is working somehow.
This omission on the part of TP-Link may safely be ignored.

---

### Post by jeremy31 on 2019-07-26
I sent an email to the maintainer of the USB ID database to get this one fixed as you can see it has no entry at [https://usb-ids.gowdy.us/read/UD/2357](https://usb-ids.gowdy.us/read/UD/2357) but it has info added at [https://usb-ids.gowdy.us/read/UD/2357/0106](https://usb-ids.gowdy.us/read/UD/2357/0106) that hasn't been approved yet

I just got a reply that the update for the Archer T9UH in the USB ID's will be added in the next 24 hours

---

### Post by jeremy31 on 2019-07-27
Try the ```
sudo update-usbids && lsusb
```
I see the update finally went through [https://sourceforge.net/p/linux-usb/repo/2706/](https://sourceforge.net/p/linux-usb/repo/2706/)

---

