---
title: "Ubuntu 7.04 server and asus wl167g"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by dolphs on 2007-05-20
Guys I am pretty new to linux and tried some things out but I get stuck configuring my asus wl167g wlan device (dmesg shows idVendor=0x0b05, idProduct = 0x1706).
I hope one can guide me a little bit through the dark.  While iinstalling Ubunutu 7.04 SERVER it comes with the error message "Attempting to find an available wireless network failed", so I assume Ubuntu does detect a device! Yet to continue I entered a Wireless ESSID for rausb0 manually, which is no problem since in my case I can find both OPEN, WEP and WPA access points with sufficient signal. Anyway I used the OPEN one to make sure it should connect, but it doesn't (while my Windows laptop does to that same AP :D)... So I assume "some network hardware is not working properly" and as said I configured the network manually. Yet I have been searching through serialmonkey's website and also ubuntu wiki but i cannot find a proper install doc to configure this WLAN in "Ubunutu 7.04 server", so I tried both serialmonkey's rt2570 and rt73 drivers, but without any joy so far...
When I install a fresh copy and do an "lsusb" it shows me "Bus 005 Device 002: ID 0b05:1706 ASUSTek Computer,Inc" so to me the device is configured but doesnt work, as said did some searches and found pieces of info, but still dead end for me; also when finding info you easily start to loose grip and maybe I have totally overlooked a perfect HOWTO to set up asus wl-167g on feisty.
Looking forward to hearing from you!

---

### Post by ruiruas on 2008-02-14
Hi,
I don't own this device, but I'm interested in buying a usb adapter and so I'm looking for the ones that work...
I've found a howto in this location. It's in portuguese, but I think you'll be able to follow the code parts.
Read it at:

[http://rdk.homeip.net/wiki/doku.php?id=wireless:asuswl-167](http://rdk.homeip.net/wiki/doku.php?id=wireless:asuswl-167)

If you can make it work, please post a new message for the comunity! :-)

---

