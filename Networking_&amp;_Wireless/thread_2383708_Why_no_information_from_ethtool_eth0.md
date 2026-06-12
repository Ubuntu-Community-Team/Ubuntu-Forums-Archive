---
title: "Why no information from ethtool eth0?"
date: 2018-01-28
forum: Networking &amp; Wireless
---

### Post by tongmengwan on 2018-01-28
[COLOR=#000000][FONT=&amp]dual boot system, win 7 and ubuntu 16.04

I used "[/FONT][/COLOR][COLOR=#000000][FONT=&amp]ethtool eth0", but I got following information. Where is wrong? Thank you ![/FONT][/COLOR][COLOR=#000000][FONT=&amp]

Cannot get device settings: No such device [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Cannot get wake-on-lan settings: No such device [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Cannot get message level: No such device [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Cannot get link status: No such device [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]No data available [/FONT][/COLOR]

---

### Post by Hadaka on 2018-01-28
Hi, please open a terminal..ctrl/alt/t...and do..
```
ifconfig | awk '/Eth/{print $1}'
```
That is your 'eth0 and wlan0'  
The definitions changed with Ubuntu 15.04
eth0 and wlan0 are no longer used.
do the ethtool command on the wired connection designation.
*It ill be something like...'enp8s0 '

---

