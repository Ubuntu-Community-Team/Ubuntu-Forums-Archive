---
title: "Sharing ethernet / Static address problem? (Dongle/USB D-Link DWL-G122 Rev. B1)"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by DARKGuy on 2007-08-15
Hey people!

I've been having a bit of a trouble configuring my D-Link wireless card. It works in Windows flawlessly, and I set it up to share my internet connection from broadband (eth0) by plugging my USB card (rausb0) and sharing the ethernet connection and clicking the "Allow other users to connect through this interface's internet connection" or something similar - this is so you can get the drift of what I want to do in Linux.

My idea is to share my ethernet connection through the wireless card using an ad-hoc connection so I can use internet on my laptop and I only have one ethernet cable, while my laptop and my PC both have wireless cards. The setup works perfectly on Windows - just not on Linux.

I've been able to get the two LEDs turn on and even scan the networks around me (found two, same ones I'll find on Windows), that's ok - using ndiswrapper. The binary driver didn't work for me.

However, I want to do what I explained above - I used to do that with two PCI realtek ethernet cards, but I don't know how to configure this USB one! :confused: I also want to use WEP encryption, and the network-admin isn't helping at all.

I've tried editing /etc/network/interfaces trying the following options (without the #'s of course):

> # auto rausb0
# iface rausb0 inet static
# address 192.168.111.1
# netmask 255.255.255.0
# wireless_essid MyESSID
# wireless_channel auto
# wireless_mode ad-hoc
# pre-up ifconfig rausb0 up
# pre-up iwconfig rausb0 channel auto
# pre-up iwconfig rausb0 essid MyESSID
# pre-up iwconfig rausb0 key MyKey
# pre-up iwconfig rausb0 essid MyESSID
> # auto rausb0
# iface rausb0 inet dhcp
# address 192.168.111.1
# netmask 255.255.255.0
# gateway 192.168.0.1
# wireless_essid MyESSID
# wireless_channel 6
# wireless_mode ad-hoc
# wireless_key MyKey
# pre-up ifconfig rausb0 up
# pre-up iwconfig rausb0 channel 6
# pre-up iwconfig rausb0 essid MyESSID
# pre-up iwconfig rausb0 key MyKey
# pre-up iwconfig rausb0 essid MyESSID
> # iface rausb0 inet static
# pre-up ifconfig rausb0 up
# wireless-essid MyESSID
# wireless-key s:MyKey
# address 192.168.1.5
# netmask 255.255.255.0
# auto rausb0
> # iface rausb0 inet dhcp
# wireless-essid MyESSID
# wireless-key s:MyKey
# auto rausb0
> # iface rausb0 inet static
# address 192.168.1.5
# netmask 255.255.255.0
# gateway 192.168.0.1
# wireless_essid MyESSID
# wireless_mode ad-hoc
# wireless_key MyKey
# auto rausb0
> auto rausb0
iface rausb0 inet static
wireless-essid MyESSID
wireless-key s:MyKey
address 192.168.1.0
netmask 255.255.255.0

With no avail.

Sometimes I get errors like this one:
> RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

And others I can't repeat right now. Sometimes my laptop can connect, but it won't get internet at all.

Any help would be greatly appreciated, I've googled all I've could before asking here.

Thanks in advance :).

---

### Post by DARKGuy on 2007-08-15
I hate to bump but... anybody? :/

---

