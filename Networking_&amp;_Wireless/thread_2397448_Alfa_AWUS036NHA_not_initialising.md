---
title: "Alfa AWUS036NHA not initialising"
date: 2018-07-29
forum: Networking &amp; Wireless
---

### Post by sidewayset on 2018-07-29
I got a the new network adapter (AWUS036NHA) and its not initializing when plugged in.

On Windows, its working fine, however on Ubuntu, it fails to start.

Here is the message from dmesg, the ligh on the adapter (blue light) is not flashing at all.

[ATTACH=CONFIG]280575[/ATTACH]

Kernel is latest version, firmware is inside /lib/firmware/htc_9271.fw
there is also ath9k_htc folder there


lsusb : recognizes the adapter and shows correctly
ifconfig: shows only my internal wifi adapter which is Intel 9260 (Killer 1550)
rfkill list all: not showing up and nothing is blocked

Extra: Ubuntu is customized to run Kali tools, as such things like Airmon-ng is not detecting it either.

Thanks for help and let me know if you need extra info

---

