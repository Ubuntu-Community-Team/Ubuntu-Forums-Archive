---
title: "Wireless USB device stops working when I restart"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by agcaruso on 2007-12-24
I am trying to set up my first linux computer as a Christmas present for my girlfriend. I have a Netgear MA111 wireless network USB device. When I first installed the driver and then plugged in the card it worked great, but when I restarted it doesn't work anymore. The computer obviously knows that it is still there because when I type 

lsusb I get: 

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0846:4110 NetGear, Inc. MA111 WiFi (v1)
Bus 001 Device 004: ID 413c:3012 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  

but it no longer sees any wireless networks. If i unplug the card, uninstall the driver, restart the computer, reinstall the driver, and then plug in the card it works well again. 

Once I have the card finding wireless networks again then I can take the card out and put it back in, and it still sees the networks, but as soon as I restart again it doesn't see any networks. 

I am quite new at linux, so if I didn't provide any information that may have been pertinent then feel free to ask and I will provide more. THank you for any help you can provide. I hope everyone out there is having a wonderful holidays.

---

### Post by rustybronco on 2007-12-24
[http://ubuntuforums.org/showpost.php?p=627259&postcount=5](http://ubuntuforums.org/showpost.php?p=627259&postcount=5)

[http://ubuntuforums.org/showthread.php?t=568468&highlight=MA111](http://ubuntuforums.org/showthread.php?t=568468&highlight=MA111)

```
 ID 0846:4110 NetGear, Inc. MA111 WiFi (v1) 
```

Your wireless device should be a prisim2 chipset, hope these posts help.
if not let me know and i'll see what I can do to help.

---

### Post by agcaruso on 2007-12-25
I installed the linux-wlan-ng as described on the second post and it made matters worse. 

Now I am not able to ndiswrapper to install or remove any drivers. I am also not able to see any networks with the wireless card. It still comes up with the thing for lsusb.

When I try to install a new driver with ndiswrapper now I get:

```
amy@amy-desktop:~$ ndiswrapper -i desktop/network driver/netma111.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

```

This is the same menu I get when I type ndiswrapper without any command. There is also no drivers shown in the graphic interface. 

I uninstalled "linux-wlan-ng" and I still have the same problems. In case it matters I also installed:
linux-wlan-ng-doc
linux-wlan-ng-firmware
linux-wlan-ng-source

Is there another area that I should be looking at to get more information on the problem? Any help will be appreciated. Even getting it back to where it works after the long ordeal would be awesome.

---

### Post by rustybronco on 2007-12-25
> **agcaruso said:**
> 
Is there another area that I should be looking at to get more information on the problem? Any help will be appreciated. Even getting it back to where it works after the long ordeal would be awesome.I would re-install the os and try this method of installing ndis from source [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
I know its more time spent but in the long run it saves a lot of effort by starting with a clean sheet to work from.

***edit*** and you could also make a startup script to automate the process of adding the driver upon a restart. i'll see if I can find out more about the process later, christmas running around you know.

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
and I would still start with a fresh sheet of paper.

---

