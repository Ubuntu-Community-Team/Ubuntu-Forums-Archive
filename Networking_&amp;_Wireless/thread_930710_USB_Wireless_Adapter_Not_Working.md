---
title: "USB Wireless Adapter Not Working"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by jethin on 2008-09-26
I have a Belkin USB Wireless adapter that I've been using to connect to open WiFi connections using manual configuration. It's been working fine but has recently crapped out. When I use ifup the device seems to connect fine to what was a fairly reliable hostname/essid, but I can't seem to transfer/receive data (I can ping localhost, but not any internet IP addresses). So:

1) How exactly can I determine where the problem lies? (the USB adapter? the open host/connection? my machine/OS?)

2) Once I figure this out, how might I correct it?

Please fire away with all your suggestions as I need to print them out and try them at home (and hopefully get a working connection!) Links to good network troubleshooting guides would be great too. Thank you.

---

### Post by shanix on 2008-09-26
First, let's take a look at your pci id for the device:

lspci -vvnn | grep Wireless

Then, tried the following command
ifconfig
ifconfig -a
iwconfig
nm-tool

---

### Post by jethin on 2008-10-20
FWIW, the problem appears to have been the host as I can now connect to another open network. One thing I've noticed about using open Wi-Fi connections: Sometimes the 'key' value is 'off' (meaning the host is open) but the bit rate is 0kbps. I don't think the listed bit rate value (retrieved via 'iwlist scan') is correct very often. Perhaps there should be (or is?) some kind of way to differentiate open connections that will pass data from those that won't.

Anyway, just my 2 cents. Otherwise this issue is 'solved'.

---

