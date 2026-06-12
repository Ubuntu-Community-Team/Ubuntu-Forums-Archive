---
title: "Corrected NATIVE Netgear WG111v2 wireless setup with Feisty (7.04) (no NDISwrapper)."
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by dan fisher on 2007-07-05
I chose the WG111v2 as it is on the compatibility table as working "out of the box" with 7.04.

The software modules are ready installed on a raw installation of feisty.  I did not want to use NDISwrapper which facilitates the windows driver for the device.

There is on the internet a set of instructions to configure two files: /etc/wpa_supplicant.conf
and /etc/network/interfaces

This is slightly incorrect.  The corrected version is shown below.  The setup is a lot more straightforward than the one using NDISwrapper.

The version from the internet has a line "inet wlan0 inet dhcp".  This should read "iface wlan0 inet dhcp".

==== start of instructions for configuring native WG111v2 driver (corrected) ====

WPA is supported in Feisty using the native module, you just need to configure it manually, instead of using NetworkManager.

The way I did it was this:

EDIT: You shouldn't need to remove NetworkManager for this to work. I didn't, and it works perfectly. I just had to remove the applet from my startup.  There is no applet in XUBUNTU.

1. Generate WPA key

wpa_passphrase <SSID> <ASCII-Key>

Where <SSID> is the SSID of your router/access point and <ASCII-Key> is the WPA key you would normally enter.

2. Copy the output from that into /etc/wpa_supplicant.conf. You should have something like this: (If the proto and key_mgmt lines aren't there add them exactly as shown)

network={
ssid="SSID"
proto=WPA
key_mgmt=WPA-PSK
psk=945609a382413e64d57daef00eb5fab3ae228716e1e440 981c004bc61dccc98c
}

3. Edit your /etc/network/interfaces file to include the following:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

4. Restart networking:

sudo /etc/init.d/networking restart

5. Enjoy your wireless! :)

==== end of instructions for configuring WG111v2 native driver ====

NOTE: The native drivers don't flash the light on the USB dongle when traffic is going through it.

:biggrin:

---

