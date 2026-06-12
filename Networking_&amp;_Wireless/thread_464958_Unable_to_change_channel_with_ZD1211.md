---
title: "Unable to change channel with ZD1211"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by fiat1100d on 2007-06-05
Hello! This is my first post here.

For university purposes I have to make some tests about WLAN security with WEP. I have set-up an Access Point (D-Link DWL-2000AP+) into channel 1, then as required I enable or disable the security.

For starting my tests, I put the following lines into /etc/network/interfaces:

auto eth1
iface eth1 inet static
address <client address>
gateway <router address>
dns-nameservers <dns address>
netmask 255.255.255.0
wireless-essid bulgakov
wireless-channel 1
wireless-mode managed

But if I try to do a sudo /etc/init.d/networking restart I get the following error:

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not permitted.

Also if I try the command "sudo iwconfig eth1 essid bulgakov" it seems that the interface associates, but the frequency is not the one of channel 1, also I frequently get the writing "Access Point: Invalid" instead of its MAC address.

From within Windows all works just fine. I need to use Ubuntu because I patched the zd1211 drivers for use with "Aircrack-ng" suite ([http://www.aircrack-ng.org](http://www.aircrack-ng.org)).

If I use network manager for connecting to another WLAN with no security all works fine (roaming mode enabled). But I need to connect to that particular AP (bulgakov) without roaming.

Thanks in advance, greetings from Italy!

---

### Post by fiat1100d on 2007-06-05
It seems I managed to solve my problems by changing the order of the lines:

auto eth1
iface eth1 inet static
wireless-essid bulgakov
wireless-key restricted s:mykey
wireless-mode managed
address <client address>
gateway <router address>
dns-nameservers <dns address>
netmask 255.255.255.0

(this is for Shared Key WEP)

In this way I don't need to specify a channel and it works. Found about the right order of the lines in this thread [http://ubuntuforums.org/showthread.php?t=288443](http://ubuntuforums.org/showthread.php?t=288443)

---

### Post by fiat1100d on 2007-06-05
I thought I solved... doesn't work again. When I try to do "networking restart" again the PC would lock when dealing with the WLAN adapter :(

---

### Post by fyrefly07 on 2007-09-05
Fiat, I believe I'm kind of in the same boat as yourself.  I'm trying to get my USB Wifi stick working with Aircrack-ng.  It uses the zd1211 drivers.  I however have not gotten past patching the drivers, although I'm beginning to second guess whether it will be necessary to do so, since the USB device does work for connecting to open networks just fine without any modification to my Ubuntu drivers.

Did you successfully apply the drivers supplied by the Aircrack project?  If so, how did you get it to work?

---

