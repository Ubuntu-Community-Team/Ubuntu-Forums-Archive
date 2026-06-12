---
title: "D-Link WDA-2320 wireless card will not start at boot"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by osx on 2008-02-09
I installed a D-Link WDA-2320 in a Dell Inspiron 530 that I bought from Dell which came preloaded with Ubuntu 7.04. After upgrading to Ubuntu 7.10 I decided to add the wireless network card. I installed it, booted the system, and it didn't work. I tried every how to I could find and it would not work. Finally, last week, I hooked the computer up to a wired connection again and installed the available updates. Suddenly, the system recognized the wireless network card, but it still would not work. I finally found enough material out there to create an "/etc/network/interfaces" configuration file like this:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid HOUSE
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <wpa key is here>

With the above configuration file, the network card works and I can get out to the Internet, but the card will not start at boot. I have to run "sudo /etc/init.d/interfaces restart" each time I reboot.

I found a suggestion to edit the grub menu.lst by adding this "pci=assign-busses' to the end of the most recent kernel line. This did not work either.

Can someone please help me with this?

---

