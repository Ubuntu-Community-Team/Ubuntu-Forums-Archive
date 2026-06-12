---
title: "[SOLVED] Wireless works, but not after reboot."
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Sydius on 2008-05-19
I am setting up two different laptops with the latest Ubuntu today.  So far, so good.  My only problem so far is that, when I reboot the computers, the wireless connection does not work until I do "sudo /etc/init.d/networking restart".  After I run that command, wireless works fine on both.  I configured both using the Network Manager.  I also tried to install the netapplet and got that working, except that it doesn't see any wireless networks until I do the "networking restart."

It's not that big of a deal to me, except that one is my girlfriend's laptop and I don't want to make her go through that every time she reboots.

Here is my etc/network/interfaces file:
```
auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wpa-psk <long hex string that I assume is the pass key>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Sydius

auto wlan0
```

Any suggestions on how to make it work on boot?

---

### Post by buccaneere on 2008-05-19
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

See post #2.

I asked the OP what different value I should use if S40 did not work, but I do not remember his answer. I imagine S50, or S60, ...

I didn't have to choose a different however.

---

