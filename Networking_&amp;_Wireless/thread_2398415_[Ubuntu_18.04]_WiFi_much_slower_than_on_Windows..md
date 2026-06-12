---
title: "[Ubuntu 18.04] WiFi much slower than on Windows."
date: 2018-08-11
forum: Networking &amp; Wireless
---

### Post by a2aaron on 2018-08-11
Hello. I am running Ubuntu 18.04 on a new Dell G7 laptop. I've noticed that the WiFi on it is extremely slow, getting less than 1 Mbps often as compared to Windows 10 (which gets up to around 100 Mbps, which is what I expected to see). Oddly enough, I am able to still use the internet, and even watch Youtube in HD without stutter. However, downloading files, even relatively small 30 MB ones, take upwards of ten minutes to an hour.

I have run the wireless info script and you can see the output of it here: [https://pastebin.com/ZmBCzNk6](https://pastebin.com/ZmBCzNk6)

Solutions I have already attempted:

I mainly attempted to follow this guide: [https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

- Disabling IPv6 - No change. I attempted to both disable IPv6 via the Settings application as well as by adding the following code in /etc/sysctl.conf
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

- Fixing the bug in the Avahi-deamon - No change. I replaced the following line in /etc/nsswitch.conf: ```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
``` with this: ```
hosts:          files dns
```

- Disabling 802.11n - Made the problem worse. I attempted to disable the 802.11n protocol by adding the following line in /etc/modprobe.d/iwlwifi.conf: ```
options iwlwifi 11n_disable=8
``` I've undone this change since then.


EDIT (Aug 13 2018): I had written "options iwlwifi 11n_disable=8"  as "options iwlwifi 11n_disable=1" by mistake before. I have since  edited my post to reflect what I really wrote.

- Adding nohwcrypt in ath9k.conf. No change. I added the following line in /etc/modprobe.d/ath9k.conf: ```
options ath9k nohwcrypt=1
```


Additional information:

I am unsure if this is related to the issue above, but on occasion, my laptop will freeze when opening an application. This also sometimes happens when shutting down. I can move the mouse but not click on anything, and the keyboard does not respond. Pressing the capslock key also does nothing. This forces me to restart the computer by holding down the power button. I suspect but can not confirm that this is an unrelated GPU driver issue as this does not happen when booting into recovery mode. This problem, also, does not occur on Windows 10.

---

### Post by mikehardy on 2018-08-12
I'm posting this in a few threads because it may be pertinent, the TL;DR is that an upgrade to the kernel, using the UKUU package, choosing kernel 4.17.14 which is the most current at the moment, fixed it for me and was otherwise painless.

[https://unix.stackexchange.com/a/462175/304207](https://unix.stackexchange.com/a/462175/304207)

---

### Post by a2aaron on 2018-08-13
Possible helpful update: When I was at friend's house today, I discovered that my laptop was getting reasonable WiFi speeds. Furthermore, when I connected my laptop to my iPhone hotspot, I got reasonable WiFi speeds again. My current network setup is a Surfboard SB 6190 (from Comcast) connecting to a Google OnHub router. When testing the WiFi speed from the Google OnHub app, I got a very fast WiFi speed, close to what I expected to see. 

My current working theory is that the connection from my laptop to the internet itself is perfectly fine, and that this is not a driver or hardware issue, but rather some sort of prioritization issue. Does anyone know if, by default, modems/routers won't prioritize network traffic to Ubuntu OSes?

(Note that even when I try to select the "prioritize this device" option in the app, it seems to have no effect on the actual speed I get.)

---

### Post by a2aaron on 2018-08-13
Update 2: After more attempts at solutions, I added

```
options iwlwifi 11n_disable = 1
```

to /etc/modprobe.d/iwlwifi.conf

This resulted in a speed up of my internet to around 10 - 20 Mbps, which is not what I expected (100+ Mbps) but is far more usable!!! Note that I wrote "= 1", not "= 8" like I had in my main post!

---

