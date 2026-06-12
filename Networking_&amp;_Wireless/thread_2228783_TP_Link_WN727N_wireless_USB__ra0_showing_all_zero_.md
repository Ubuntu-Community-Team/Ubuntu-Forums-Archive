---
title: "TP Link WN727N wireless USB:  ra0 showing all zero mac address"
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by lahirister on 2014-06-09
I am trying to get a TP Link WN727N working with Ubuntu 12.10 (quantal) and is not able to go past a certain point. Any help will be appreciated. Here are the details on what I have tried and observed so far. Please note because it is on a system with no network connectivity it is not possible to copy/paste output:

Installed rt2870sta module
Blacklisted:
rt2800usb
rt2x00lib
rt2x00usb

lsusb shows the TP Link device
modinfo rt2870sta shows the correct mod alias (vendor name: product name combination seen in lsusb)
lshw -C network shows the TP Link device with network DISABLED
iwconfig shows ra0 interface
ifconfig shows ra0 (but with all 00 mac address)
/var/log/syslog and dmesg shows the following error:
[COLOR=#545454][FONT=arial]NICLoadFirmware: [/FONT][/COLOR][COLOR=#545454][FONT=arial]**MCU**[/FONT][/COLOR][COLOR=#545454][FONT=arial] is [/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#545454]**not ready**[/COLOR][/SIZE][/FONT]

[FONT=arial][SIZE=2][COLOR=#545454]I have also tried to replace the rt2870.bin firmware with the one from the MediaTek website without success.[/COLOR][/SIZE][/FONT]
[FONT=arial][SIZE=2][COLOR=#545454]Tried to also use rt2x00 and rt2800usb modules without success.[/COLOR][/SIZE][/FONT]

[FONT=arial][SIZE=2][COLOR=#545454][B]I believe if I can get ifconfig to show the real mac address (not all zeroes) of the TP Link device I will be good.
[/B]Any idea please let me know.[B]

Thanks[/B][/COLOR][/SIZE][/FONT]

---

