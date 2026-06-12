---
title: "tune up networking upon startup"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by macubo on 2007-06-05
Hi all, I was able to make my eth0 and wlan0 fully working.. but i recognize (by temporary toggling the "quiet splash" boot parameters) that now the "configuring network interface" entry upon startup takes too long to be executed (approx. 25 secs).

Moreover even with my wireless on upon startup, when i want to use it I have to issue the command "sudo /etc/init.d/networking restart"or, "sudo ifdown wlan0" and then "sudo ifup wlan0".

Something similar is required for eth0.

I guess that upon startup the system tries to get a valid IP (as they are configured for DHCP in "/etc/network/interfaces") and waits for it. 

Well this is not a major issue but i'd like to speed the boot process up.
Thank you

Now a few outputs:
```
manuele@manuele-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid **hidden**
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk **hidden**

```

```
manuele@manuele-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:b0:c3:50:f4 arp 1
wlan0 mac 00:14:a5:69:66:35 arp 1

```

---

### Post by macubo on 2007-06-05
ehm.... solved thanks to "man interfaces"
Just modified interfaces this way:
```
manuele@manuele-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid **hidden**
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk **hidden**

```

By the way, what are those strange interfaces I commented out, eth2 and ath0? They aren't present in iftab. And.. does the eth0 interface have to be present in /etc/network/interfaces to be brought up by (sudo) ifup eth0?

---

